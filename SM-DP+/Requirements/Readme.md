1. SMDP1 [Void]
2. SMDP2 The SM-DP+ SHALL be able to initiate the request for ISD-P creation as part of the Bound Profile Package delivery.
3. SMDP3 The SM-DP+ SHALL establish an end-to-end secure channel to the eUICC to download and install Bound Profile Packages on the eUICC.
4. SMDP4 The SM-DP+ SHALL link a Protected Profile Package for binding to a specific eUICC only at the request of the respective Operator.
5. SMDP5 The SM-DP+ SHALL create a Bound Profile Package from the linked Protected Profile Package only at the request of the respective eUICC.
6. SMDP6 The SM-DP+ SHALL be able to create a Bound Profile Package for any Certified eUICC.
7. SMDP7 Only the target eUICC SHALL be able to decrypt the content of a Bound Profile Package delivered by the SM-DP+.
8. SMDP8 Profile Packages SHALL only leave the SM-DP+ after completing all production steps, Profile Package Protection, and binding.
9. SMDP9 Communication session between the SM-DP+ and the LPA SHALL be terminated by the SM-DP+ after execution of intended Operation(s).
10. SMDP10 End-to-end communication between the SM-DP+ and the eUICC involved in the Profile download and installation SHALL be protected in terms of integrity, authenticity and confidentiality.
11. SMDP11 Profile Packages stored within the SM-DP+ SHALL always be protected through encryption.
12. SMDP12 On the SM-DP+, backups as well as used data within the Profile creation and storage infrastructure SHALL be discarded using secure deletion procedures (logically and physically).
13. SMDP13 SM-DP+/eUICC communication SHALL incorporate Perfect Forward Secrecy (PFS).
14. SMDP14 The transport used for the Bound Profile Package SHALL implement anti-replay mechanisms between the SM-DP+ and the eUICC.
SMDP14a The SM-DP+ SHALL check the information referenced by the digital identification in ELG26.
15. SMDP15 Connectivity to the SM-DP+ SHALL be aborted and an explicit error message SHALL be triggered by the SM-DP+ upon failure to verify authenticity or failure to verify the information referenced by the digital identification in ELG26 of the connecting party. (No message SHALL be sent to the connecting party)
16. SMDP16 After a configurable number of failed attempts to download a Bound Profile Package to the LPA, the transport encryption procedure SHALL be renewed. If subsequent attempts to download the Bound Profile Package fail more than a configurable number of times, the provisioning transaction SHALL be terminated and the Mobile Service Provider and the supporting Operator SHALL be notified.
17. SMDP17 The SM-DP+ SHALL use a secure version of Internet protocols whenever available (e.g. DNSSEC, DNSCurve, etc.).
18. SMDP18 The SM-DP+ SHALL prepare Profile Packages following the eUICC Profile Package Interoperable Format Specification as defined by Trusted Connectivity Alliance [5].
19. SMDP19 The SM-DP+ SHALL be able to create Bound Profile Packages on demand.
20. SMDP20 It SHALL be possible for the SM-DP+ to create Profile Packages in bulk.
21. SMDP21 The SM-DP+ SHALL send a confirmation of the successfully completed download and installation of a Profile to the Mobile Service Provider and the supporting Operator.
22. SMDP22 There SHALL be a mechanism to remove any relationship between any SM-DP+ and the ISD-P following the successful installation of the Profile. Such a mechanism SHALL either be ordered by the Operator or be performed by the Operator itself. If such deletion mechanism is used, there will be no off-card entity responsible for managing the ISD-P of the installed Profile.
23. SMDP23 The SM-DP+ SHALL be globally uniquely identified by its SMDPid.
24. SMDP24 The SM-DP+ Certificate SHALL include the SMDPid.
25. SMDP25 The SM-DP+ SHALL be able to send a Notification to the Operator informing them that a specific Bound Profile Package download is starting. Such notifications MAY be forwarded by the Operator to the Mobile Service Provider.
26. SMDP26 The SM-DP+ SHALL be able to send an Eligibility Check Information report and other relevant information (e.g. Activation Code, ICCID, etc.) to the Mobile Service Provider and the supporting Operator ahead of/prior to the eUICC Bound Profile Package download.
SMDP26a Before a Profile download, the SM-DP+ SHALL be able to check whether the eUICC has enough memory to install the Profile.
27. SMDP27 The SM-DP+ SHALL be able to perform Event Registrations to the SMDS that is requested by the Operator.
SMDP27a It SHALL be possible for the SM-DP+ to indicate to the Operator lists of Root SM-DSs and Alternative SM-DSs to which the SM-DP+ can perform the (possibly cascaded) Event Registration associated with an RSP operation.
Note: This could be part of the static configuration between the SM-DP+ and the Operator.
SMDP27b It SHALL be possible for the Operator to indicate to the SM-DP+, the Root SM-DS to which the SM-DP+ performs the (possibly cascaded) Event Registration associated with an RSP operation.
SMDP27c It SHALL be possible for the Operator to indicate to the SM-DP+ that an Event Registration be cascaded and indicate the Alternative SM-DS to be used.
28. SMDP28 The SM-DP+ SHALL be able to request an Alternative SM-DS not to cascade an Event Registration to a specific Root SM-DS.
29. SMDP29 The SM-DP+ SHALL be able to send a Profile delete Notification to the Mobile Service Provider and the supporting Operator owning a Profile when a related delete Notification is received from the eUICC.
30. SMDP30 The SM-DP+ SHALL support the following states for a Profile Package, triggered by the Profile Owner:
• A Profile Package is not released for Profile Package download.
• A Profile Package is released for Profile Package download.
31. SMDP31 The SM-DP+ SHALL be able to select the elliptic curve parameter in the Profile download procedure.
32. SMDP32 (FFS) [Void]
33. SMDP33 (FFS) [Void]
34. SMDP34 (FFS) [Void]
35. SMDP35 (FFS) [Void]
36. SMDP36 A SM-DP+ SHALL support all sets of elliptic curve parameters for the CAs that it uses.
37. SMDP37 If a Profile Package is not yet released for download then the LPA, SHALL be informed by means of a specific error code.
38. SMDP38 An SM-DP+ SHALL be able to distinguish a Field-Test eUICC from a Certified eUICC through eUICC Eligibility Check Information.
39. SMDP39 The SM-DP+ SHALL be able to be instructed by the Profile Owner to reject an RSP operation to Field-Test eUICCs.
Note: The mechanism is out of the scope of this document and it is left to implementation.
40. SMDP40 The SM-DP+ SHALL NOT perform an RSP operation to a Field-Test eUICC if it has been instructed so by the Profile Owner as per SMDP49.
41. SMDP41 The Managing SM-DP+ SHALL be able to send a Notification to the Profile Owner informing them that a requested RPM command is about to be executed.
42. SMDP42 Only a Managing SM-DP+ SHALL be allowed to perform RPM on a Profile.
43. SMDP43 If RPM is supported by the Managing SM-DP+, the LPA and the eUICC: the Managing SM-DP+ SHALL establish a secure channel to the eUICC to perform Remote Profile Management (RPM) providing authentication, authorisation, and integrity checking. Ciphering SHALL be provided between the SM-DP+ and the LPA.
44. SMDP44 The SM-DP+ SHALL be able to send a Profile enabled Notification to the Mobile Service Provider and the supporting Operator owning a Profile when a related enabled Notification is received from the eUICC.
45. SMDP45 The SM-DP+ SHALL be able to send a Profile disabled Notification to the Mobile Service Provider and the supporting Operator owning a Profile when a related disabled Notification is received from the eUICC.
46. SMDP46 The SM-DP+ SHALL provide means for the Operator to query about the current status of a Profile Package. The search criteria and level of details of the returned information are implementation-dependent.
47. SMDP47 In the Event Registration, the SM-DP+ SHALL indicate to the SM-DS the RSP operation type (i.e., Profile download or RPM).
48. SMDP48 In the Event Registration, the SM-DP+ SHALL be able to provide to the SM-DS information that can be used by the LPA to identify the target Profile(s) upon Event Retrieval.
Note: See BAS7 and the text at the beginning of Basic Principles 2.1 for privacy requirements to be covered.
49. SMDP49 The information in SMDP48 SHALL NOT disclose to the SM-DS any private or confidential data of the target Profile.
50. SMDP50 In the Event Registration, the SM-DP+ SHALL be able to provide the Mobile Service Provider Name to the SM-DS to be forwarded to the LPA upon Event Retrieval.
51. SMDP51 The SM-DP+ SHOULD ensure that repeated Profile or RPM download attempts due to expired/outdated Event Records are prevented (as per SMDP52 and SMDP53).
52. SMDP52 The SM-DP+ SHALL request the deletion of the associated Event Record (if any) of a successful Profile or RPM download.
53. SMDP53 The SM-DP+ SHOULD request the deletion of the associated Event Record (if known) of an expired/outdated Profile or RPM download attempt.
