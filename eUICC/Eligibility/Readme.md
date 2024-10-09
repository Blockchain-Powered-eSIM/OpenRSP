Eligibility Check enables an SM-DP+ to validate the eligibility of an eUICC and the Device for the installation of a Profile using information sent by the eUICC.  
The set of information sent by the eUICC to the SM-DP+ for Eligibility Checking purposes is referenced herein as the Eligibility Check Information.  
Some Eligibility Check parameters MAY be required due to Device capabilities which must be supported by the Profile/eUICC and delivered as part of the Eligibility Check Information set.
Note: Device capability refers to a Device feature or service-enabling function provided by the Device that MAY have a direct effect on the content of the Profile or the procedure used to download the Profile, and consequently requires support from the eUICC.

1. **ELG1** The eUICC SHALL indicate the specification versions it is supporting. This parameter SHALL be transmitted to the SM-DP+ during the Eligibility Check.  
2. **ELG2** The eUICC SHALL include the available memory in the Eligibility Check Information.  
3. **ELG3** The eUICC SHALL declare in the Eligibility Check Information if it is unable to accept an additional Profile.
4. **ELG4** The eUICC SHALL provide a valid current Certificate to the SM-DP+ signed by the EUM.
5. **ELG5** The eUICC SHALL provide an identification of the EUM.
6. **ELG6** The eUICC SHALL provide the current OS version in the Eligibility Check Information.
7. **ELG7** The eUICC SHALL provide in the Eligibility Check Information, Device enabler information relating to services that may require Profile support (e.g. NFC enablers).
8. **ELG8** Eligibility Check Information SHALL be integrity and authenticity protected by the eUICC before it is sent to the SM-DP+.
9. **ELG9** The eUICC SHALL indicate the application runtime environment version and libraries versions supported in Eligibility Check Information.
10. **ELG10** The eUICC SHALL indicate cryptographic algorithms and their respective key lengths supported in the Eligibility Check Information.
11. **ELG11** The eUICC SHALL declare in the Eligibility Check Information the list of supported CIs.
12. **ELG12** [Void]
13. **ELG13** The eUICC SHALL declare in the Eligibility Check Information if it is a NFC eUICC.
14. **ELG14** [Void]
15. **ELG15** An eUICC SHALL provide information indicating if it is a Discrete eUICC or an Integrated eUICC.
16. **ELG16** An eUICC SHALL indicate in the Eligibility Check Information if it is a Field-Test eUICC.
17. **ELG17** The eUICC SHALL declare which LPA Mode is being used during the secure session with the SM-DP+.
18. **ELG18** The eUICC SHALL declare in the Eligibility Check Information if it supports eUICC OS Update.
19. **ELG19** The eUICC SHALL declare permitted Profile Policy Rules in the Eligibility Check Information.
20. **ELG20** The Eligibility Check Information MAY include the Device’s IMEI.
21. **ELG21** Eligibility Check Information SHALL include the Device Type allocation code.
22. **ELG22** Eligibility Check Information SHALL include the Device radio access technologies, including release.
23. **ELG23** The eUICC SHALL declare the eUICC Form Factor Type in the Eligibility Check Information.
24. **ELG24** Eligibility Check Information SHALL include the Device letter class(es) according to 3GPP TS 31.111 [33] and ETSI TS 102 223 [34].
25. **ELG25** When the Device is Enterprise Capable, this SHALL be indicated in the Eligibility Check Information
26. **ELG26** There SHALL be a means to retrieve the certifications (functional and security) of the eUICC
