## Basic Principles
1. **BAS1** Existing standards and specifications SHALL be used where possible for the specification of the eUICC and related provisioning systems.
2. **BAS2** GlobalPlatform specifications SHALL be used as a framework of choice for the implementation of the eUICC.
3. **BAS3** The overall security of the eUICC in combination with the relatedmanagement processes SHALL at all times and under all circumstances be at least equivalent to the current removable UICC and its provisioning processes.
4. **BAS4** The architecture of the eUICC and its Remote SIM Provisioning system SHALL comply with the requirements of 3GPP TS 33.102, 3GPP TS 33.401 and 3GPP TS 33.501.
5. **BAS5** The architecture SHALL support a level of security with respect to the protection of Operator Credentials which is at least equivalent to the present levels of security. This applies in particular to:
• the confidentiality of cryptographic keys and authentication parameters;
• the integrity of Subscriber identities (e.g. IMSI).
6. **BAS6** The architecture SHALL support a level of security for all Profile content which is at least equivalent to the current state of the art level of security of the UICC.
7. **BAS7** The architecture SHALL NOT compromise the security and privacy of Subscriber Data, nor the security and privacy of End User Data. Examples depending on territory include identities that can be used for tracking such as ICCID, MSISDN, EID, IMSI, Ki etc.
8. **BAS8** Regulatory issues are considered outside the scope of this document. However, any data which could be used to identify an individual SHALL be treated as personal data and subject to local regulations e.g. the EID, ICCID, IMEI, IMSI etc
9. **BAS9** The RSP Session SHALL prevent sending IMEI and EID information to a non-authenticated RSP Server.
10. **BAS10** The SM-DP+ acts on behalf of the Profile Owner.

## Profile Requirements
1. **PRO3** A Profile SHALL be uniquely identified by its ICCID.
2. **PRO4** An Enabled Profile in combination with an eUICC SHALL be able to carry all logical characteristics of a UICC.
3. **PRO5** Once the Profile is enabled, all relevant UICC characteristics or features as described in ETSI 102 221 [2] specifications SHALL apply, with the exceptions as defined within this specification.
4. **PRO6** It SHALL be possible to delete Profiles only when in a disabled state, with the exception of eUICC Memory Reset, and eUICC Test Memory Reset functions.
5. **PRO8** A Profile SHALL be either an Operational Profile or a Test Profile.
