# eUICC

The internal high-level architecture of the eUICC.
The eUICC architecture is similar to that used in the GSMA Remote SIM Provisioning of Embedded UICC Technical specification.
Profiles are provisioned based on the security framework defined in the GlobalPlatform Card Specification.

[Schematic Representation of the eUICC](https://www.gsma.com/solutions-and-impact/technologies/esim/wp-content/uploads/2023/12/SGP.21-V3.1.pdf)  
<img width="608" alt="Screenshot 2024-10-03 at 10 27 14 PM" src="https://github.com/user-attachments/assets/a7aede0b-8945-4bc1-945c-66c0d3139730">

## ECASD
The Embedded UICC Controlling Authority Security Domain (ECASD) is responsible for the secure storage of credentials needed to support the required security domains on the eUICC.
There SHALL only be one ECASD on an eUICC. The ECASD SHALL be installed and personalised by the EUM during the eUICC manufacturing as described in GlobalPlatform Card Specification.
The ECASD SHALL contain the following:
• eUICC private keys for creating signatures.
• Associated Certificates for eUICC Authentication.
• The Certificate Issuers’ (CI) root public keys for verifying SM-DP+ and SM-DS
Certificates.
• eUICC Manufacturers’ (EUMs) keyset for key/Certificate renewal.
Additionally, the ECASD SHALL provide security functions used during key establishment and eUICC Authentication.

## ISD-R
The ISD-R is responsible for the creation of new ISD-Ps and the lifecycle management of all ISD-Ps.

## ISD-P
The ISD-P is a secure container (security domain) for the hosting of a Profile.  
The ISD-P is used for Profile download and installation in collaboration with the Profile Package interpreter for the decoding/interpretation of the received Bound Profile Package. The ISD-P is the on-card representative of the SM-DP+.

## MNO-SD
The MNO-SD is the on-card representative of the Operator which issued the Profile. It contains the Operator’s Over-The-Air (OTA) Keys and provides a secure OTA channel.

## Profile Policy Enabler
The eUICC Operating System (OS) service which offers Profile Policy Rules validation and enforcement.

## Telecom Framework
The telecom framework is an operating system service that provides standardised network authentication algorithms to the NAAs hosted in the ISD-Ps. Furthermore, it offers the capability to configure the algorithms with the necessary parameters.

## Profile Package Interpreter
The Profile Package interpreter is an eUICC operating system service that translates the Profile Package data into an installed Profile using the
specific internal format of the target eUICC.

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
