1. EUICC1 : The eUICC SHALL be a discrete or integrated tamper resistant component consisting of hardware and software, capable of securely hosting applications as well as confidential and cryptographic data.
Note: Wherever a distinction is required, the former is referred to as Discrete eUICC, and the latter as Integrated eUICC.
2. EUICC2 : A removable eUICC is packaged in a standardised ETSI Form Factor.
3. EUICC3 : The Discrete eUICC SHALL be either removable or non-removable.
4. EUICC4 : The behaviour of the eUICC with an Enabled Profile SHALL be equivalent to the UICC.
5. EUICC5 : The eUICC SHALL be able to contain zero or more Profiles.
6. EUICC6 : [Void]
7. EUICC7 : The behaviour of a NAA USIM, ISIM or CSIM within a Profile on an eUICC SHALL be identical to a removable UICC NAAs USIM, ISIM or CSIM.
Note: No changes to existing 3GPP/3GPP2 USIM, CSIM and ISIM specifications are expected.
8. EUICC8 : The eUICC SHALL support Milenage and TUAK algorithm sets.
9. EUICC9 : The EUM Keyset shall be issued by the EUM.
10. EUICC10 : If any Profile Management operation does not complete successfully, the eUICC SHALL maintain the state it was in before it received the request.
11. EUICC11 : The eUICC SHALL contain an ECASD security domain as well as an ISD-R security domain installed and personalised during manufacture.
12. EUICC12 : It SHALL NOT be possible to delete or disable the ECASD after eUICC manufacture.
13. EUICC13 : The ISD-R SHALL be responsible for the creation of new ISD-Ps and the lifecycle management of all ISD-Ps.
14. EUICC14 : The ISD-R SHALL be installed and personalised by the EUM during eUICC manufacturing as described in GlobalPlatform Card Specification.
15. EUICC15 : The eUICC SHALL support an eUICC Memory Reset.
16. EUICC16 If the eUICC supports Test Profiles, the eUICC SHALL support eUICC Test Memory Reset.
17. EUICC17 : The eUICC SHALL support the eUICC Profile Package Interoperable Format Specification as defined by Trusted Connectivity Alliance.
18. EUICC18 : An ISD-R SHALL:
• NOT be deleted or disabled;
• NOT be able to perform any operations inside an ISD-P.
19. EUICC19 : An eUICC MAY provide LPA functions.
20. EUICC20 : An ISD-P SHALL be created by the ISD-R at the request of the SM-DP+.
21. EUICC21 : Communication between the eUICC and the SM-DP+ SHALL be protected in authenticity, integrity and confidentiality.
22. EUICC22 : The eUICC SHALL NOT export Profiles installed on the eUICC.
23. EUICC23 : The eUICC SHALL enforce an isolation of Profiles and prevent Profiles from operating outside of their execution environment i.e. Profile SHALL run in a sandbox.
24. EUICC24 : The integrity of the Bound Profile Package SHALL be ensured during its installation on the eUICC.
25. EUICC25 : [Void]
26. EUICC26 : Profile keys and algorithm parameters SHALL NOT be extractable from the eUICC.
27. EUICC27 : All cryptographic functions SHALL be implemented in a robust tamperresistant way and be resistant to side-channel attacks.
28. EUICC28 : [Void]
29. EUICC29 : A downloaded Profile Package SHALL be installed on the eUICC in a disabled state.
30. EUICC30 : The eUICC SHALL always report its eSVN in the first communication during the commencement of each session with the SM-DP+ or SM-DS.
31. EUICC31 : The EUM SHALL install an eUICC Certificate in the eUICC to authenticate the eUICC.
32. EUICC32 : The EUM SHALL install an EUM Certificate in the eUICC to verify the eUICC Certificate.
33. EUICC33 : The eUICC SHALL have a means to authenticate itself to the SM-DS.
34. EUICC34 : [Void]
35. EUICC35 : Upon Profile deletion, the eUICC SHALL ensure a complete deletion of all data related to the Profile.
36. EUICC36 : The eUICC SHALL only accept Profile Management operations sent from the LPA (in either the eUICC, or the Device), and from Managing SM-DP+s.
37. EUICC37 : The eUICC SHALL reject any Profile Management operations that are in conflict with the Profile Policy Rules of the respective Profile.
38. EUICC38 : If any Bound Profile Package download or installation does not complete successfully, the eUICC SHALL maintain the state it was in before it received the request.
39. EUICC39 [Void]
40. EUICC40 : The eUICC SHALL be able to store one or more default SM-DP+ address(es).
41. EUICC41 : The eUICC SHALL be able to store one or more Root SM-DS addresses.
EUICC41a : A removable eUICC SHALL have at least one Root SM-DS address configured.
42. EUICC42 : The eUICC SHALL be able to send a delete Notification to the LPA to notify the Notification Receivers that the Profile has been deleted.
43. EUICC43 : In EUICC42, if connectivity is not available to send the Notification of deletion to the Notification Receivers, each Notification SHALL be retained and sent as soon as connectivity becomes available again.
44. EUICC44 : The delete Notification process SHALL also be executed for each deleted Profile in case of eUICC Memory reset.
45. EUICC45 : The eUICC SHOULD support Java Card. If supported, the specifics of these functions and features SHALL be explicitly referenced within the technical specification (SGP.22).
46. EUICC46 : The eUICC SHALL support USIM Toolkit functions and GlobalPlatform features. The specifics of these functions and features SHALL be explicitly referenced within the technical specification (SGP.22).
47. EUICC47 :  An eUICC SHALL support at least two elliptic curves preloaded by the EUM during eUICC manufacturing.
48. EUICC48 : Each Notification SHALL be uniquely identifiable and SHALL be signed by the eUICC.
49. EUICC49 : Each Notification SHALL be protected against re-play attacks and signed by the eUICC.
50. EUICC50 : [Void]
51. EUICC51 : [Void]
52. EUICC52 : The Profile SHALL be able to contain a list of zero or more Notification Receivers for each type of Notification.
53. EUICC53 : [Void]
54. EUICC54 : The EID SHALL NOT be modifiable. The EID SHALL NOT be affected by any of the procedures, including the change of eUICC Private keys.
55. EUICC55 : An Integrated eUICC SHALL be certified according to SGP.08 or SGP.18 as described in SGP.24.
56. EUICC56 : The Integrated eUICC SHALL be based on an Integrated TRE.
57. EUICC57 : An Integrated eUICC SHALL be able to execute the test cases defined in SGP.23.
EUICC57a : The Integrated eUICC SHALL allow the SM-DP+ to identify the type of the Integrated TRE including its component configuration (e.g. use of internal or Remote Memory, use of other optional components), its manufacturer, in addition to the RSP OS provider.
EUICC57b : The Integrated TRE SHOULD have priority access to Remote Memory in cases of shared resource contention.
EUICC57c : The Integrated eUICC Test Interface SHALL be compatible with commonly used interfaces for smartcard testing.
58. EUICC58 : For the purpose of integration and/or end-to-end testing, a Field-Test eUICC MAY contain certificates that chain up to the GSMA CI.
59. EUICC59 : The eUICC MAY provide a means by which the Profile Owner of an Enabled Profile can request the LPA to check for Events (Root SM-DS(s)) or pending RSP operations (Default SM DP+(s)).
60. EUICC60 : The eUICC MAY provide a means by which the Profile Owner of an Enabled Profile can request the LPA to check for Events or pending RSP operations on the Polling Address configured in the Enabled Profile.
61. EUICC61 : The eUICC SHALL support the ‘set/edit nickname’ function.
62. EUICC62 : The eUICC SHALL support at least one eSIM CA for:
- Profile binding
- mutual authentication between eUICC and SM-DP+
- mutual authentication between eUICC and SM-DS.
63. EUICC63 : An eUICC MAY support SM2, SM3 and SM4 cryptographic algorithms, for mutual authentication and data encryption between the SM-XX and eUICCs.
Note: TLS is used between the LPA and the SM-XX and is not considered in this requirement.
64. EUICC64 : A non-removable eUICC MAY support Multiple Enabled Profiles (MEP). 
NOTE: Support of Multiple Enabled Profiles on a removable eUICC is FFS.
65. EUICC65 : The eUICC MAY provide a means by which the LPA is able to determine the current estimated size of an installed Profile.
66. EUICC66 : An eUICC SHOULD support Interoperable Applications.
67. EUICC67 : An eUICC implementing EUICC66 SHALL support an application runtime environment facilitating interoperability, e.g. Java Card. The application runtime environment(s) SHALL be explicitly indicated to the SM-DP+.
68. EUICC68 :  The Enabled/Disabled state of a Profile SHALL remain unchanged when the eUICC undergoes the following operations outside of an ‘Enable Profile’ or ‘Disable Profile’ procedure:
- Powering down or powering up the eUICC
- Removing the eUICC from the Device
- Inserting the eUICC in the Device (whether the same Device or a different Device)
