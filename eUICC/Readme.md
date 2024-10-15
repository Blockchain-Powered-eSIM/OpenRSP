# eUICC
The RSP architecture is based on existing SIM functionality and smartcard security concepts (as defined by ETSI and GlobalPlatform). These allow the eUICC to operate akin to a standard SIM whilst affording RSP management from the off-card entity: the remote provisioning server.
The eUICC security domain architecture comprises the following elements 

- The eUICC Controlling Security Domain *(ECASD)* represents the off card entity `Certificate Issuer (CI)`
- The Issuer Security Domain - Root *(ISD-R)* represents the off-card entity `SM-SR`
- The Issuer Security Domain - Profile *(ISD-P)* hosts a profile, representing the off-card entity `SM-DP`

[Schematic Representation of the eUICC](https://www.gsma.com/solutions-and-impact/technologies/esim/wp-content/uploads/2023/12/SGP.21-V3.1.pdf)  
<img width="608" alt="Screenshot 2024-10-03 at 10 27 14 PM" src="https://github.com/user-attachments/assets/a7aede0b-8945-4bc1-945c-66c0d3139730">

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
The MNO-SD is the on-card representative of the Operator which issued the Profile. It contains the Operator’s Over-The-Air (OTA) Keys and provides a secure OTA channel.
The primary component of a “Profile” is the MNO-SD, representing the network operator with their Over-The-Air (OTA) Keys and provides a secure OTA channel. Other components include configurations to support use of Network Access Applications (NAA), supplementary security domain (SSD), policy rules (POL1) and connectivity parameters.

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
