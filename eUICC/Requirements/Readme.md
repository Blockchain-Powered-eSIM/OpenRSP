EUICC1 : The eUICC SHALL be a discrete or integrated tamper resistant component consisting of hardware and software, capable of securely hosting applications as well as confidential and cryptographic data.
Note: Wherever a distinction is required, the former is referred to as Discrete eUICC, and the latter as Integrated eUICC.

EUICC2 : A removable eUICC is packaged in a standardised ETSI Form Factor [2].

EUICC3 : The Discrete eUICC SHALL be either removable or non-removable.

EUICC4 : The behaviour of the eUICC with an Enabled Profile SHALL be equivalent to the UICC.

EUICC5 : The eUICC SHALL be able to contain zero or more Profiles.

EUICC6 : [Void]

EUICC7 : The behaviour of a NAA USIM, ISIM or CSIM within a Profile on an eUICC SHALL be identical to a removable UICC NAAs USIM, ISIM or CSIM.
Note: No changes to existing 3GPP/3GPP2 USIM, CSIM and ISIM specifications are expected. 

EUICC8 : The eUICC SHALL support Milenage [11][12] and TUAK [10] algorithm sets.

EUICC9 : The EUM Keyset shall be issued by the EUM.

EUICC10 : If any Profile Management operation does not complete successfully, the eUICC SHALL maintain the state it was in before it received the request.

EUICC11 : The eUICC SHALL contain an ECASD security domain as well as an ISD-R security domain installed and personalised during manufacture.

EUICC12 : It SHALL NOT be possible to delete or disable the ECASD after eUICC manufacture.

EUICC13 : The ISD-R SHALL be responsible for the creation of new ISD-Ps and the
lifecycle management of all ISD-Ps.

EUICC14 : The ISD-R SHALL be installed and personalised by the EUM during eUICC manufacturing as described in GlobalPlatform Card Specification [9].

EUICC15 : The eUICC SHALL support an eUICC Memory Reset.

EUICC16 If the eUICC supports Test Profiles, the eUICC SHALL support eUICC Test Memory Reset.

EUICC17 : The eUICC SHALL support the eUICC Profile Package Interoperable Format Specification as defined by Trusted Connectivity Alliance [5].

EUICC18 : An ISD-R SHALL:
• NOT be deleted or disabled;
• NOT be able to perform any operations inside an ISD-P.

EUICC19 : An eUICC MAY provide LPA functions.

EUICC20 : An ISD-P SHALL be created by the ISD-R at the request of the SM-DP+.

EUICC21 : Communication between the eUICC and the SM-DP+ SHALL be protected in authenticity, integrity and confidentiality.

EUICC22 : The eUICC SHALL NOT export Profiles installed on the eUICC.

EUICC23 : The eUICC SHALL enforce an isolation of Profiles and prevent Profiles from operating outside of their execution environment i.e. Profile SHALL run in a sandbox.
EUICC24 : The integrity of the Bound Profile Package SHALL be ensured during its installation on the eUICC.
EUICC25 : [Void]
EUICC26 : Profile keys and algorithm parameters SHALL NOT be extractable from the eUICC.
EUICC27 : All cryptographic functions SHALL be implemented in a robust tamperresistant way and be resistant to side-channel attacks.
EUICC28 : [Void]
EUICC29 : A downloaded Profile Package SHALL be installed on the eUICC in a disabled state.
EUICC30 : The eUICC SHALL always report its eSVN in the first communication during the commencement of each session with the SM-DP+ or SM-DS.
EUICC31 : The EUM SHALL install an eUICC Certificate in the eUICC to authenticate the eUICC.
EUICC32 : The EUM SHALL install an EUM Certificate in the eUICC to verify the eUICC Certificate.
EUICC33 : The eUICC SHALL have a means to authenticate itself to the SM-DS.
EUICC34 : [Void]
EUICC35 : Upon Profile deletion, the eUICC SHALL ensure a complete deletion of all data related to the Profile.

EUICC36 : The eUICC SHALL only accept Profile Management operations sent from the LPA (in either the eUICC, or the Device), and from Managing SM-DP+s.
EUICC37 : The eUICC SHALL reject any Profile Management operations that are in conflict with the Profile Policy Rules of the respective Profile.
EUICC38 : If any Bound Profile Package download or installation does not complete
successfully, the eUICC SHALL maintain the state it was in before it
received the request.
EUICC39 [Void]

EUICC40 : The eUICC SHALL be able to store one or more default SM-DP+ address(es).

EUICC41 : The eUICC SHALL be able to store one or more Root SM-DS addresses.

EUICC41a : A removable eUICC SHALL have at least one Root SM-DS address configured.

EUICC42 : The eUICC SHALL be able to send a delete Notification to the LPA to notify the Notification Receivers that the Profile has been deleted.

EUICC43 : In EUICC42, if connectivity is not available to send the Notification of deletion to the Notification Receivers, each Notification SHALL be retained and sent as soon as connectivity becomes available again.

EUICC44 : The delete Notification process SHALL also be executed for each deleted Profile in case of eUICC Memory reset.

EUICC45 : The eUICC SHOULD support Java Card. If supported, the specifics of these functions and features SHALL be explicitly referenced within the technical specification (SGP.22 [24]).
EUICC46 : The eUICC SHALL support USIM Toolkit functions and GlobalPlatform features. The specifics of these functions and features SHALL be explicitly referenced within the technical specification (SGP.22 [24]).

EUICC47 :  An eUICC SHALL support at least two elliptic curves preloaded by the EUM during eUICC manufacturing.

EUICC48 : Each Notification SHALL be uniquely identifiable and SHALL be signed by the eUICC.

EUICC49 : Each Notification SHALL be protected against re-play attacks and signed by the eUICC.

EUICC50 : [Void]

EUICC51 : [Void]

EUICC52 : The Profile SHALL be able to contain a list of zero or more Notification Receivers for each type of Notification.

EUICC53 : [Void]

EUICC54 : The EID SHALL NOT be modifiable. The EID SHALL NOT be affected by any of the procedures, including the change of eUICC Private keys.

EUICC55 : An Integrated eUICC SHALL be certified according to SGP.08 [56] or SGP.18 [57] as described in SGP.24 [27].

EUICC56 : The Integrated eUICC SHALL be based on an Integrated TRE.

EUICC57 : An Integrated eUICC SHALL be able to execute the test cases defined in SGP.23 [47].

EUICC57a : The Integrated eUICC SHALL allow the SM-DP+ to identify the type of the Integrated TRE including its component configuration (e.g. use of internal or Remote Memory, use of other optional components), its manufacturer, in addition to the RSP OS provider.

EUICC57b : The Integrated TRE SHOULD have priority access to Remote Memory in cases of shared resource contention.

EUICC57c : The Integrated eUICC Test Interface SHALL be compatible with commonly used interfaces for smartcard testing.

EUICC58 : For the purpose of integration and/or end-to-end testing, a Field-Test eUICC MAY contain certificates that chain up to the GSMA CI.

EUICC59 : The eUICC MAY provide a means by which the Profile Owner of an Enabled Profile can request the LPA to check for Events (Root SM-DS(s)) or pending RSP operations (Default SM DP+(s)).

EUICC60 : The eUICC MAY provide a means by which the Profile Owner of an Enabled Profile can request the LPA to check for Events or pending RSP operations on the Polling Address configured in the Enabled Profile.

EUICC61 : The eUICC SHALL support the ‘set/edit nickname’ function.

EUICC62 : The eUICC SHALL support at least one eSIM CA for:
• Profile binding
• mutual authentication between eUICC and SM-DP+
• mutual authentication between eUICC and SM-DS.

EUICC63 : An eUICC MAY support SM2, SM3 and SM4 cryptographic algorithms, defined in [35], [36] and [37] for mutual authentication and data encryption between the SM-XX and eUICCs.

Note: TLS is used between the LPA and the SM-XX and is not considered in this requirement.

EUICC64 : A non-removable eUICC MAY support Multiple Enabled Profiles (MEP). 

NOTE: Support of Multiple Enabled Profiles on a removable eUICC is FFS.

EUICC65 : The eUICC MAY provide a means by which the LPA is able to determine the current estimated size of an installed Profile. 

EUICC66 : An eUICC SHOULD support Interoperable Applications.

EUICC67 : An eUICC implementing EUICC66 SHALL support an application runtime environment facilitating interoperability, e.g. Java Card. The application runtime environment(s) SHALL be explicitly indicated to the SM-DP+.

EUICC68 :  The Enabled/Disabled state of a Profile SHALL remain unchanged when the eUICC undergoes the following operations outside of an ‘Enable Profile’ or ‘Disable Profile’ procedure:
• Powering down or powering up the eUICC
• Removing the eUICC from the Device
• Inserting the eUICC in the Device (whether the same Device or a different Device)
