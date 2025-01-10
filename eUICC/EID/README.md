# EID Definition and Assignment Process

## Introduction to EID

The eUICC Identifier (EID) is an unique global serial number for eUICCs. The EID is not related to services and subscriptions. Initially the format for EID was inherited from the Integrated Circuit Card Identifier (ICCID) format where certain fields of the ICCID were embedded in the EID structure.

The ICCID is defined by [ITU-T E.118](https://www.itu.int/rec/T-REC-E.118-200605-I/en) as a Primary Account Number (PAN) and within ICCID there is an Issuer Identifier Number (IIN). However, the EID is not a PAN, as it is not meant for charging services. National authorities issue IINs/ICCIDs under various rules, leading to challenges for manufacturers, including difficulties in obtaining EIDs in certain cases.

## eUICC Numbering System

The length of EID is fixed at 32 digits. The composition for a compliant EID is given below

![EID Structure](./../../assets/images/EID_Structure.png "EID Structure")  
EID Structure

Breaking down each component of EID Structure

- The EUM Identity Number (EIN) → N digits (variable length)
    - The EIN is composed of one or more concatenated EID Range Holder Identifiers (ERHIx), with the final ERHI assigned to an EUM
    - Each ERHI is allocated by an EIN Assignment Authority (EAA) to either an EUM or another EAA
    - The EAA ensures that the ERHIs it assigns are unique
    - ERHIs that are assigned do not need to have a uniform length
    - The EAA decides how many digits the assigned ERHIs will contain. For example, if ERHI 11 is assigned to entity A, ERHIs 110 to 119 or any other number starting with 11 can no longer be assigned, but ERHIs 120 to 129 can be allocated to entities B through K
    - The GSMA acts as first level EAA
    - GSMA will assign ERHI1s to
        - EUMs
        - National Authorities
        - Device Manufacturers
        - Group of Device Manufacturers
    - Examples on chain of ERHIs:
        - The GSMA assigns ERHI1 to an EAA, the EAA assigns ERHI2 values to Device Manufacturers (identified by their GSMA-assigned ERHI1 value), and the Device Manufacturer assigns ERHI3 to an EUM (identified by the EAA-assigned ERHI2 value).
        - The GSMA assigns ERHI1 to a Device Manufacturer, and the Device Manufacturer assigns ERHI2 values to an EUM (identified by its GSMA-assigned ERHI1 value).
        - The GSMA assigns ERHI1 to a Group of Device Manufacturers, the Group assigns ERHI2 values to a single Device Manufacturer (identified by its GSMA-assigned ERHI1 value), and the single Device Manufacturer assigns ERHI3 to an EUM (identified by its EAA-assigned ERHI2 value).
- The EUM Specific Identification Number (ESIN) → 30 - N digits (variable length, depends on EIN)
    - ESINs are assigned by EUM
    - EUM assures that assigned ESINs are unique
- The Check digits → 2 check digits calculated by EUM over all 32 digits
    - Set initial value of check digits as zero
    - Using the resulting 32 digit EID (decimal integer), compute modulo 97
    - Subtract the resulting modulo value from 98 and use the resulting value as heck digits (if result is only one digit then pad it by prefixing 0 as first check digit)

> **EIDs can be verified using it as a 32 digit decimal integer and performing modulo 97 for it. If the result is 1 then the EID is valid, otherwise the verification fails.**

## Criteria for ERHI1 Assignment

The following criteria has to be met by an entity to get an ERHI1 assigned to it

- The applicant applying for an ERHI1 SHALL NOT already have an ERHI1 assigned
to it, except in the justified exceptions
- The applicant SHALL commit to use ERHI1 (within 12 months of release date)
- For Non-National Authorities
    - The applying entity SHALL be an EUM or (Group of) Device Manufacturers
    AND
    - Applicant SHALL be a single corporate entity operating under a specific legislative regulation.

### ERHI1 Assignment Process

![ERHI Level1 Assignment](./../../assets/images/ERHI1_assignment.png "ERHI Level 1 Assignment Process")  
ERHI Level 1 Assignment

The Process is defined by GSMA as follows:

1. Form Filling
2. Submission
Completed registration forms are sent to [EISRegistration@gsma.com](mailto:EISRegistration@gsma.com)
3. Verification
GSMA verifies the authenticity of applicant company and the validity of application
4. Assignment/Rejection
On the basis of Verification result in Step 3, GSMA assigns the ERHI1
5. GSMA Confirmation

### ERHI1 Cancellation Process

![ERHI1 Cancellation](./../../assets/images/ERHI1_cancellation.png "ERHI1 Cancellation Process")  
ERHI1 Cancellation

In addition to the EIN Assignment Process, an ERHI1 that is no longer used by a company
may be cancelled by the EIN Assignment Authority. The process for this as defined by GSMA is

1. Form Filling
2. Submission
Completed cancellation forms are sent to [EISRegistration@gsma.com](mailto:EISRegistration@gsma.com)
3. Verification Process
4. GSMA Confirmation

---
### eUICC Identifier (EID)

The eUICC Identifier (EID) is a globally unique serial number assigned to eUICCs, distinct from service-related identifiers like subscriptions. Initially, its format was derived from the Integrated Circuit Card Identifier (ICCID), with specific fields from the ICCID embedded within the EID structure. Unlike the ICCID, which is defined as a Primary Account Number (PAN) for services (as per [ITU-T E.118](https://www.itu.int/rec/T-REC-E.118-200605-I/en)), the EID is not intended for charging purposes. The assignment of IINs/ICCIDs varies by country, leading to challenges for manufacturers, including obtaining EIDs in some cases.

#### Structure of EID

An EID is a 32-digit identifier made up of three main components:
![EID Structure](./assets/images/EID_Structure.png "EID Structure")  
EID Structure

##### EUM Identity Number (EIN)
- The EIN is composed of one or more concatenated EID Range Holder Identifiers (ERHIx), with the final ERHI assigned to an EUM.
- ERHIs are allocated by an EIN Assignment Authority (EAA), which can assign them to an EUM or another EAA.
- ERHIs vary in length and are assigned in a manner that ensures their uniqueness. The EAA determines how many digits the ERHI will contain.
- **Example**: If ERHI 11 is assigned to entity A, numbers starting with 110 to 119 are no longer available, but 120 to 129 can be allocated to other entities.
- The GSMA acts as the first-level EAA and assigns ERHI1s to EUMs, National Authorities, Device Manufacturers, or Groups of Device Manufacturers.

##### EUM Specific Identification Number (ESIN)
- The ESIN makes up the remaining digits of the EID (30 minus the length of the EIN) and is assigned by the EUM.
- The EUM ensures that each ESIN it assigns is unique.

##### Check Digits
- Two check digits are calculated by the EUM for the full 32-digit EID. These check digits are derived by calculating the modulo 97 of the EID and subtracting the result from 98.
- If the result is only one digit, a zero is prefixed to make two digits.

> **EIDs can be verified by performing a modulo 97 operation. If the result is 1, the EID is valid.**

#### ERHI Assignment and Examples

The ERHI assignment process involves several steps:
- The GSMA assigns ERHI1 to an EAA, which can then assign ERHI2 values to Device Manufacturers. These manufacturers may assign ERHI3 to EUMs.
- Alternatively, GSMA may assign ERHI1 directly to Device Manufacturers, who then assign ERHI2 to EUMs.
- In cases where ERHI1 is assigned to a Group of Device Manufacturers, they can distribute ERHI2 values to individual manufacturers, who then assign ERHI3 to EUMs.

#### Example ERHI Assignments

- **Example 1**: The GSMA assigns ERHI1 to an EAA. The EAA assigns ERHI2 values to Device Manufacturers, who assign ERHI3 to EUMs.
- **Example 2**: The GSMA assigns ERHI1 directly to a Device Manufacturer, who assigns ERHI2 values to EUMs.
- **Example 3**: The GSMA assigns ERHI1 to a Group of Device Manufacturers, who assign ERHI2 values to individual manufacturers, and these manufacturers assign ERHI3 to EUMs.
---

## References

- [Abbreviations](./References/Abbreviations.md)
- [Definitions](./References/Definitions.md)
- [EID Principles](./References/Principles.md)
- [EID Requirements](./References/Requirements.md)
- [ITU-T E.118](https://www.itu.int/rec/T-REC-E.118-200605-I/en)
- [ISO/IEC 7812-1](https://www.iso.org/standard/70484.html)
- [GSMA SGP.29 - EID Definition](https://www.gsma.com/solutions-and-impact/technologies/esim/wp-content/uploads/2024/03/SGP.29-v1.1.pdf)
