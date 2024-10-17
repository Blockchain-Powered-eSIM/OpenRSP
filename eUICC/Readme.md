# eUICC
The RSP architecture is based on existing SIM functionality and smartcard security concepts (as defined by ETSI and GlobalPlatform). These allow the eUICC to operate akin to a standard SIM whilst affording RSP management from the off-card entity: the remote provisioning server.
The eUICC security domain architecture comprises the following elements 

- The eUICC Controlling Security Domain *(ECASD)* represents the off card entity `Certificate Issuer (CI)`
- The Issuer Security Domain - Root *(ISD-R)* represents the off-card entity `SM-SR`
- The Issuer Security Domain - Profile *(ISD-P)* hosts a profile, representing the off-card entity `SM-DP`

[Schematic Representation of the eUICC](https://www.gsma.com/solutions-and-impact/technologies/esim/wp-content/uploads/2023/12/SGP.21-V3.1.pdf)  
<img width="608" alt="Screenshot 2024-10-03 at 10 27 14 PM" src="https://github.com/user-attachments/assets/a7aede0b-8945-4bc1-945c-66c0d3139730">

The eUICC (embedded Universal Integrated Circuit Card) is the core component of RSP protocol. The eUICC enables remote management and switching of mobile network operator profiles on devices without needing a physical SIM swap. It allows multiple profiles to be downloaded, activated, and managed over the air, providing flexibility for IoT devices, smartphones, and wearables. This simplifies connectivity across different networks, supports multi-operator use cases, and enhances efficiency for operators and users alike.
The eUICC architecture has similarities to GSMA Remote SIM Provisioning of Embedded UICC Technical specification. Profiles are provisioned in `SGP.21` compliant RSP systems based on the security framework defined in the GlobalPlatform Card Specification.
There are certain requirements for eUICC module laid out by GSMA describing behavior and supported functionality to the eUICC implementation be viable for RSP solution. These requirements are listed [here](https://github.com/Blockchain-Powered-eSIM/OpenRSP/tree/main/eUICC/Requirements).
There are many sub-components of the eUICC module along with an Operating System which manages the interactions of eUICC to the device and RSP server components.

## ECASD
The Embedded UICC Controlling Authority Security Domain (ECASD) is responsible for the secure storage of credentials needed to support the required security domains on the eUICC.  
The ECASD is installed by the EUM (eUICC Manufacturer) in personalisation stage of manufacturing process. The ECASD contains a unique eUICC-ID (EID) including embedded codes for country, issuer and unit identification. The EUM also installs a certificate for authentication, a public key for verifying certificate signatures and a private key for elliptic curve cryptography.

There SHALL only be one ECASD on an eUICC. The ECASD SHALL be installed and personalised by the EUM during the eUICC manufacturing as described in GlobalPlatform Card Specification.
The ECASD SHALL contain the following:
- eUICC private keys for creating signatures.
- Associated Certificates for eUICC Authentication.
- The Certificate Issuers’ (CI) root public keys for verifying SM-DP+ and SM-DS Certificates.
- eUICC Manufacturers’ (EUMs) keyset for key/Certificate renewal.
  Additionally, the ECASD SHALL provide security functions used during key establishment and eUICC Authentication.

## ISD-R
The ISD-R is also installed by EUM, it is associated with the ECASD and it is the only component with visibility and access to ISD-P. Upon very strict conditions and instructions, the ISD-R creates, enables, disables and deletes ISD-P’s and also provides functions for secure channel setup between SM-DP and ISD-P. ISD-R also manages the fallback profile (if there is any).  
The ISD-R is responsible for the creation of new ISD-Ps and the lifecycle management of all ISD-Ps.

## ISD-P
The Issuer Security Domain - Profile or ISD-P is a secure containerised domain for hosting a Profile. The ISD-P is created by ISD-R using Profile Package Interpreter (part of eUICC OS) for decoding of the received Bound Profile Package. ISD-P represents the on-card equivalent of SM-DP+.

## MNO-SD
The MNO-SD is the on-card representative of the Operator which issued the Profile. The primary component of a “Profile” is the MNO-SD, representing the network operator with their Over-The-Air (OTA) Keys and provides a secure OTA channel. Other components include configurations to support use of Network Access Applications (NAA), supplementary security domain (SSD), policy rules (POL1) and connectivity parameters.
![Please contact repo maintainers to update images](https://github.com/Blockchain-Powered-eSIM/OpenRSP/blob/main/assets/images/ISD-P_profileStructure.png "Profile Structure Overview")

## Profile Policy Enabler
The eUICC Operating System (OS) service which offers Profile Policy Rules validation and enforcement.

## Telecom Framework
The telecom framework is an eUICC operating system service that provides standardised network authentication algorithms to the NAAs hosted in the ISD-Ps. Furthermore, it offers the capability to configure the algorithms with the necessary parameters.

## Profile Package Interpreter
The Profile Package interpreter is an eUICC operating system service that translates the Profile Package data into an installed Profile using the specific internal format of the target eUICC.

## LPA Services
The LPA services provide necessary access to the services and data required by the LPA functions for the following:
1. The Root SM-DS address.
2. The optionally stored default SM-DP+ address(es).
3. Facilitates the reception of the Bound Profile Package in transfer from the LPA.
4. Provides information regarding the installed Profiles and their Profile Metadata.
5. Provides Local Profile Management
6. Supports Remote Profile Management operations
7. Provides functions for the LPA to authenticate and interact with the SM-DS.
8. Ensures access to the EID is restricted to only the LPA.

## Interfaces
There are several interface defined by the RSP specification which covers interactions between different system components of RSP. In this section only interfaces which involve eUICC and the device LPA are defined.
General Interface Requirements are listed [here](https://github.com/Blockchain-Powered-eSIM/OpenRSP/blob/main/Interfaces/Requirements.md).

## Compliance
Compliance with GSMA standards for eUICC manufacturing and operations is strictly required as per current implementation of RSP specifications. The compliance procedure for M2M and Consumer RSP solutions are different.

> OpenRSP's primary focus is the consumer RSP solution.

### M2M eUICC Compliance
[Compliance](https://www.gsma.com/iot/embedded-sim/compliance/) with GSMA M2M specification requires verification of
- eUICC Security, referencing a Common Criteria Protection Profile to the assurance level of EAL4+ [Reference](https://www.commoncriteriaportal.org/https://www.gsma.com/newsroom/wp-content/uploads/SGP_05_v1_1.pdf).
- Production environment and Process security, via the GSMA’s SAS. SAS-UP (for eUICC personalisation) or SAS-SM (for subscription management platforms). [Reference](https://www.gsma.com/sas).
- Functional Compliance based on [GSMA test specification](https://www.gsma.com/iot/wp-content/uploads/2014/10/SGP-11-Remote-Provisioning-Architecture-for-Embedded-UICC-Test-Specification.pdf)

### Consumer RSP Solution
[Compliance](https://www.gsma.com/solutions-and-impact/technologies/esim/compliance/) with consumer solution requires verification of
- eUICC security using the same mechanisms as M2M specification. Initial focus is on a [silicon-level protection file](https://www.commoncriteriaportal.org/files/ppfiles/pp0084a_pdf.pdf). GSMA has also publishes eUICC security measures principles and methodology in documents `SGP.06` and `.07`.
- Production environment and process security is through SAS-UP or SAS-SM according to the consumer solution entity type.
- Functional compliance for all consumer entities is maintained via functional test and certification programs based o GSMA specification `SGP.23`. These programmes have been established, in partnership with GSMA, by GlobalPlatform (for eUICC), Global Certification Forum and PTCRB (for Consumer solution devices).

The GSMA PRD `SGP.24` details the compliance requirements, and expected means to demonstrate compliance, for product designed to the eSIM specifications, `SGP.22` and `SGP.21`. `SGP.24` also provides declaration templates to be completed and submitted to GSMA once an eSIM product has proven its compliance by test and/or certification

The compliance requirements focus on security assurance, functionality and interoperability. The result of a successful `SGP.24` declaration of compliance is a recognised achievement plus eligibility to use an eSIM Digital Certificate (PKI). This is used for authentication between eUICCs and eSIM Subscription Management servers (SM-DP+ and SM-DS).

#### Security Assurance by design
The eUICC IC/hardware platform requirement is [Common Criteria](https://www.commoncriteriaportal.org/) certification to the Security IC Platform Protection Profile with Augmentation Package Certification (`PP-0084` or `PP-0117`). Certification to `PP-0035` is also acceptable.

All GSMA eSIM compatible eUICCs that follow the industry GSMA eSIM Specifications (as defined in `SGP.21` and `SGP.22`), have to prove robustness by complying with `SGP.25`. The permitted methodologies architecture
- Common Criteria `PP-0100` Certification report reference.
- GSMA eSA Certification reference (eUICC Security Accreditation Scheme)

#### Security Assurance in production and SM service location
GSMA SAS is required for security accreditation for eSIM entities handling sensitive assets such as MNO profile, digital certificates etc. For eUICCs SAS-UP audits are applicable and for SM-DP+ (and SM-DS) the equivalent is SAS-SM audit.
