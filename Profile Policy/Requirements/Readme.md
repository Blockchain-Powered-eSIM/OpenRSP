## Test Profile Requirements

1. TPRO1 It is OPTIONAL for the eUICC to support the requirements of Test Profiles described in this section. If Test Profiles are not supported, it SHALL NOT be possible to download Test Profiles into the eUICC.
2. TPRO2 Test Profiles SHALL NOT be able to authenticate to an Operator’s mobile network using Operator Credentials. The eUICC SHALL ensure that such Profiles cannot be used to connect to any Operator’s mobile network even if authentication information is contained in the Test Profile.
3. TPRO3 A Test Profile SHALL be installed in its own individual ISD-P.
4. TPRO4 Test Profiles MAY be pre-installed on the eUICC.
5. TPRO5 Test Profiles SHALL only be visible and usable when the Device is in Device Test Mode.
6. TPRO6 It SHALL be possible to download, install, enable, disable or delete Test Profiles in the eUICC only in Device Test Mode with the exception of the eUICC Memory Reset operation.
7. TPRO7 Test Profiles, as with any other Profile, SHALL be managed through a certified SM-DP+.
8. TPRO8 The enabling of a Test Profile SHALL override the ‘Disabling of this Profile is not allowed’ (POL RULE1) Profile Policy Rule.
9. TPRO9 When the Device Test Mode is deactivated, the LPA SHALL disable any enabled Test Profile.
10. TPRO10 When the Test Profile is disabled, the eUICC SHALL enable the
11. Operational Profile that was previously enabled, if any.
12. TPRO11 The Device Test Mode activation SHALL be obfuscated from the End User.
13. TPRO12 When exiting Device Test Mode, an End User notice SHALL be presented to prompt the tester to perform an eUICC Test Memory Reset.
