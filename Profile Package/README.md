# Introduction

This documents specifies a technical specification for a standard format to be used for loading and installation of an interoperable Profile Package in a compliant eUICC. 

The eUICC (embedded UICC) and other components of remote provisioning system need to perform numerous functions in an open remote ecosystem which were previously carried out in personalisation centres of UICC vendors. To enable this a Profile is used in RSP solution to represent the functionality and configuration offered by UICC based SIM card modules for a subscription.

The Profile Package, represents the structure of data to be built by the Profile Creator and to be loaded in the eUICC in order for the eUICC to be personalised according to the content of the Profile Package. 

> **NOTE: Profile Package definition does not support 2G SIM applications by default.**

# Profile Package General Structure

The Profile Package is a collection of **Profile Elements (PE)** which use a common description language independent of the transfer protocol. Each PE can be described and processed independently on compatible eUICCs (some PEs require a specific sequence as they need context of previous PEs to be processed).  An identification number is associated with every PE which can be used for accurate error reporting. Some examples of Profile Elements are: profile header, NAA, file system etc.

The description of every PE in this specification is based on ASN.1 specified in [[X.680]](https://www.itu.int/rec/T-REC-X.680-202102-I) and encoded in TLV (Tag Length Value) structures using DER (Distinguished Encoding Rule) encoding as specified in [[X690]](https://www.itu.int/rec/T-REC-X.690-202102-I/en).

## Error Management

A Profile Element (PE) can be marked to indicate that supporting the feature described by the PE is mandatory. If the eUICC doesn’t support this feature, an error is sent to the Profile Creator, the Profile Package processing is stopped, and any already processed PEs will be discarded by the eUICC. If a PE is not flagged as mandatory, and the eUICC cannot install it or doesn’t support the feature, a warning will be issued, but the Profile Package processing may continue. The status message coding for this process is also defined later in this document.

To prevent errors and warnings during Profile Package processing, the Profile Creator can audit the eUICC before building the Profile Package. This ensures that all features described in the Profile Package are fully supported by the eUICC, making the Profile installation more predictable. If this audit is skipped, the Profile may still function, but some features could be restricted.

The eUICC features required to install the Profile are also listed in the Profile header. If the eUICC doesn’t support any of these features, it will return an error and immediately stop processing the Profile. This serves as a second check, particularly for features not included in the standardised list (such as proprietary features). This second mechanism complements the list of mandatory features encoded in the Profile header and is required for some specific features (e.g. proprietary features) that are not in the standardised list of features

If a Profile Package is incorrectly defined (e.g., PEs not provided in the correct order, missing mandatory fields, or attempting to create an existing file), the behavior of the eUICC is not clearly specified. This could result in a Profile with unexpected behavior or failure of the installation, regardless of whether the PE is mandatory.

## ASN.1 Module

The PE format is defined in a single, self-contained, ASN.1 definition module called "`PEDefinitions`", with an ISO Object Identifier in the Trusted Connectivity Alliance namespace

```
-- ASN1START
PEDefinitions {joint-iso-itu-t(2) international-organizations(23) tca(143)
euicc-profile(1) spec-version(1) version-three(3)}
DEFINITIONS
AUTOMATIC TAGS
EXTENSIBILITY IMPLIED ::=
BEGIN
EXPORTS UICCCapability; -- Definition to be used in remote provisioning
specifications for eligibility check
-- ASN1STOP
```

Breaking down the module:

1. Module Name
    1. `PEDefinitions` is the name of the module
    2. `{joint-iso-itu-t(2) international-organizations(23) tca(143) euicc-profile(1) spec-version(1) version-three(3)}` is an Object Identifier (OID) for this module
2. Definitions
    1. `DEFINITONS` marks the start of ASN.1 definition
    2. `AUTOMATIC TAGS` means that the tags are defined automatically using the encoding rules unless a tag notation is present in the PE format definition
    3. `EXTENSIBILITY IMPLIED` means that data types may contain additional elements not part of this specification. This is useful for processing PEs from a newer version of the specification. If an eUICC has to process these unknown values then it should either report a warning or an error using the code `invalid-parameter` as defined later in this document.
3. Begin and Exports
    1. `BEGIN` marks the start of ASN.1 module’s body
    2. `EXPORTS UICCCapability` specifies that the type ‘UICCCapability’ is available for use by other modules.

Proprietary tags shall not be used inside the PEs defined in this specification, except inside `PENonStandard`.

## IoT Minimal Profile Package

IoT Minimal Profile Package is meant for use in limited network bandwidth configurations. IoT profile allows provisioning of a simple package with a reduced number of PEs. The simplifications used by IoT Minimal Profile Package are:

- The Profile header contains an additional element `iotOptions`, including the PIX value which is used to create USIM AID
- `PE-IoT` is used to create a simplified file system. This file system is suitable for the provisioning of a basic USIM configuration. Additional optional files can also be created using other PEs (e.g. `PEOPT-IoT`, `PE-GenericFileManagement`). PE-MF is not allowed. The file system shall be defined using at least the `PE-IoT`
- The PIN and PUK values do not need to be specified in case default values suffice
- Default access rules are defined. These rules can be modified, extended or replaced if required.

## Full Profile Package

This Profile Package type is used in all applications in which network bandwidth is not a limitation. For Full Profiles, the Profile Header shall NOT include the field `iotOptions`, `PE-IoT` and `PE-OPT-IoT`.

# Profile Package Elements Definition

## Common Types

### General Purpose Types

The maximum allowed size of integers, octet strings and other data types which are referenced in other PE definitions are defined in this module to avoid ambiguity.

```
-- ASN1START
-- Basic integer types, for size constraints
maxUInt8 INTEGER ::= 255
UInt8 ::= INTEGER (0..maxUInt8)
maxUInt15 INTEGER ::= 32767
UInt15 ::= INTEGER (0..maxUInt15)
maxUInt16 INTEGER ::= 65535
UInt16 ::= INTEGER (0..maxUInt16)
maxUInt31 INTEGER ::= 2147483647
UInt31 ::= INTEGER (0..maxUInt31)
-- ASN1STOP
```

### Profile Specific Types

These types are referenced in other PE definitions as well.

```
-- ASN1START
ApplicationIdentifier ::= OCTET STRING (SIZE(5..16))
-- ASN1STOP
```

### PE Header

The PE Header is present at the beginning of all PEs described in this specification. A PE Header broadly contains the following information

- PE Identification Number
- Optional flag indicating mandatory support
- PE Type
- PE Length

```
-- ASN1START
PEHeader ::= SEQUENCE {
mandated NULL OPTIONAL,
-- if set, indicate that the support of this PE is mandatory
identification UInt15 -- Identification number of this PE
}
-- ASN1STOP
```

`mandated` field indicates that the support for this PE is mandatory for the Profile to be provisioned onto an eUICC. If an eUICC cannot process a PE with this tag, it shall abort the processing of the Profile and return an error to Profile sender. The `identification` field shall be unique.

The following snippet is a list of supported PEs

```
-- ASN1START
ProfileElement ::= CHOICE {
	header ProfileHeader,
/* PEs */
	genericFileManagement PE-GenericFileManagement,
	pinCodes PE-PINCodes,
	pukCodes PE-PUKCodes,
	akaParameter PE-AKAParameter,
	cdmaParameter PE-CDMAParameter,
	securityDomain PE-SecurityDomain,
	rfm PE-RFM,
	application PE-Application,
	nonStandard PE-NonStandard,
	end PE-End,
	rfu1 PE-Dummy, -- this avoids renumbering of tag values
	rfu2 PE-Dummy, -- in case other non-file-system PEs are
	rfu3 PE-Dummy, -- added here in future versions
	rfu4 PE-Dummy,
	rfu5 PE-Dummy,
/* PEs related to file system creation using templates defined in this
specification */
	mf PE-MF,
	cd PE-CD,
	telecom PE-TELECOM,
	usim PE-USIM,
	opt-usim PE-OPT-USIM,
	isim PE-ISIM,
	opt-isim PE-OPT-ISIM,
	phonebook PE-PHONEBOOK,
	gsm-access PE-GSM-ACCESS,
	csim PE-CSIM,
	opt-csim PE-OPT-CSIM,
	eap PE-EAP,
	df-5gs PE-DF-5GS,
	df-saip PE-DF-SAIP,
	df-snpn PE-DF-SNPN,
	df-5gprose PE-DF-5GPROSE,
	iot PE-IoT,
	opt-iot PE-OPT-IoT,
...
}

PE-Dummy ::= SEQUENCE {
}
-- ASN1STOP
```

To ensure PEs are not sent in an order which creates unresolved dependencies during installation the following rules should be considered by the Profile Creator:

1. Profile Header  
Shall be the first element and provided only once in a Profile download
2. PE-MF  
May be provided once as the first element of the file system creation after the `ProfileHeader` in a Full Profile. If this PE is not used, the MF shall be created as the first element of the file system using the `PEGenericFileManagement` in a Full Profile. `PE-MF` is not allowed in the IoT Minimal Profile.
3. PE-CD  
This is optional and shall come after the creation of MF
4. PE-TELECOM  
This is optional and shall come after the creation of MF
5. PE-USIM  
This is optional and shall come after the creation of MF
6. PE-OPT-USIM  
This is optional and shall come after the creation of an ADF USIM
7. PE-ISIM  
This is optional and shall come after the creation of MF
8. PE-OPT-ISIM  
This is optional and shall come after the creation of an ADF ISIM
9. PE-GSM-ACCESS  
This is optional and shall come after the creation of an ADF USIM
10. PE-PHONEBOOK  
This is optional and shall come after the creation of an ADF USIM
11. PE-DF-5GS  
This is optional and shall come after the creation of an ADF USIM
12. PE-DF-SAIP  
This is optional and shall come after the creation of an ADF USIM
13. PE-DF-SNPN  
This is optional and shall come after the creation of an ADF USIM
14. PF-DF-5GPROSE  
This is optional and shall come after the creation of an ADF USIM
15. PE-CSIM  
This is optional and shall come after the creation of MF
16. PE-OPT-CSIM  
This is optional and shall come after the creation of an ADF CSIM
17. PE-IoT  
Shall be included once as first element of file system after `ProfileHeader` in an IoT Minimal Profile. Shall not be used in a Full Profile
18. PE-OPT-IoT  
This is optional and shall come after `PE-IoT`
19. PE-GenericFileManagement  
Dependencies within the file system creation should be considered when using this PE
20. PE-AKAParameters  
If this PE is provided, it shall be present in the context of the creation of a NAA filesystem. It may be provided once or several times per NAA. If several sets of parameters are provided for one NAA, the set of parameters used by this NAA is not defined. This element is not allowed in the context of MF, SDs and applications.
21. PE-PINCodes  
PIN codes shall be created in context of their scope. Global PINs (Application PINs as per [ETSI TS 102 221](https://www.etsi.org/deliver/etsi_ts/102200_102299/102221/18.02.00_60/ts_102221v180200p.pdf)) and Local PINs shall be provided once in PIN Context of creation of MF of UICC and DF/ADF respectively. The "PIN Context" is fixed by the first ADF/DF created by the previous PE which contains an ADF/DF using PE-Template or PEGeneric File Management.
`PE-PINCode` and `pinStatusTemplateDO` usage adheres to the following rules
    1. Every Global PINs referenced by a `pinStatusTemplateDo` shall be defined in the PIN Context of the MF
    2. All Local PINs referenced by a `pinStatusTemplateDo` shall be either defined in a parent ADF/DF or created in a subsequent `PE-PINCodes`
    3. If the usage rules are not satisfied, the eUICC shall abort Profile processing and return the error code `pin-code-missing`
22. PE-PUKCodes  
May only be provided once within the context of the UICC file system (MF). It needs to include all PUK codes for the complete profile. If this PE is not present in the Profile Package then no PUK codes are defined.
23. PE-SecurityDomain  
Should be created after the creation of the file system, NAA parameters and PIN/PUK configuration
24. PE-Application  
Shall be provided after associated application’s SD is created
25. PE-RFM  
Shall be provided after the creation of SDs
26. PE-NonStandard  
May be provided in any position after Profile Header, exact restrictions vary on the application 
27. PE-End  
Shall be provided once at the end of Profile Package
28. PE-EAP  
Use of this PE is optional. If used, it shall come after creation of the ADF which supports EAP.
