## Profile Metadata Requirements

1. **META1** All Profiles SHALL have associated Profile Metadata.
2. **META2** Unless specified otherwise in the below requirements, the Profile Metadata SHALL be stored in the eUICC.
3. **META3** The Profile Metadata SHALL be accessible irrespective of the state of the Profile.
4. **META4** The Profile Metadata SHALL include a field for the Mobile Service Provider name.
Note: EFSPN is already used in a different context outside of this specification and could be blank.
5. **META5** The Profile Metadata SHALL include a field for the ICCID of the Profile.
6. **META6** The Profile Metadata SHALL include a field for the End User nickname of the Profile.
7. **META7** The Profile Metadata SHALL include a field for containing a short description of the Profile defined by the Operator or Mobile Service Provider.
8. **META8** [Void]
9. **META9** The Profile Metadata SHALL always be available to the LPA. The display to the End User is implementation-specific.
10. **META10** The Profile Metadata SHALL include an OPTIONAL field to allow the display of an icon defined by the Operator or Mobile Service Provider for the respective Profile.
11. **META11** Profile Metadata SHALL be able to include a copy of the Profile Policy Rules associated to the Profile.
**META11a** The Profile Metadata SHALL be able to include a message that is to be displayed to the End User when the Profile contains a Profile Policy Rule. It SHALL NOT be stored after Profile download.
12. **META12** All Profiles SHALL be uniquely identified in the Profile Metadata as Operational, Provisioning or Test Profile.
13. **META13** An Operator, potentially on behalf of a Mobile Service Provider SHALL be able to access and update the following Profile Metadata of its Profile using the ES6 interface if the Profile is Enabled:
• Mobile Service Provider name
• Short description of the Profile
• Icon of the Profile
• HR icon reference
• List of Managing SM-DP+ and their respective authorisations to update individual Profile Metadata items
• Profile Owner OIDs that are allowed to implicitly disable this Profile by RPM ‘Enable’
• Polling Address
• Profile Policy Rules (unset only)
• Enterprise ID (access only)
• Enterprise Name
• Enterprise Rules
• Device Change Configuration of the Profile
The content of the respective Profile SHALL reflect the updated Profile Metadata.
14. **META14** The Profile Metadata SHALL include an OPTIONAL field (named HR icon reference) that enables access to high resolution icons. The icons MAY be hosted by the SM-DP+ that handles the Profile.
15. **META15** The HR icon reference SHALL allow the LPA to retrieve one or several icons for a Profile in the format(s) best suited for presentation on the user interface. Best fitting icons are intended to be shown during Profile download, Profile selection etc.
16. **META16** The HR icon solution SHALL provide an option to allow the HR icon(s) to be provided during the Profile download procedure.
17. **META17** The Profile Metadata SHALL include an OPTIONAL field for Device Change Configuration of the Profile. This field SHALL include OPTIONAL sub-fields for:
• The address of the SM-DP+ that processes Device Change request
• The Activation Code to be used by the new Device for Device Change
• An indication of whether the Profile has to be deleted before the Activation Code is made available for the new Device, where the Activation Code is either from the present sub-field or what was used to trigger the original Profile Download procedure.
Note: If an Activation Code is present in the sub-field, then it supersedes the Activation Code that was used to trigger the original Profile Download procedure.
18. **META18** The Profile Metadata SHALL be able to include an optional field for the estimated installed size of the Profile.
19. **META19** The Profile Metadata SHALL be able to include a list of Managing SMDP+(s).
20. **META20** The Profile Metadata SHALL include an optional field to allow for the inclusion of the Enterprise ID.
21. **META21** The Profile Metadata SHALL include an optional field to allow for the inclusion of the Enterprise Name.
22. **META22** The Profile Metadata SHALL be able to include additional proprietary information. The additional proprietary information SHALL include a field for uniquely identifying the issuer of the additional proprietary information.
23. **META23** With regard to META22, the eUICC SHALL ignore fields it does not support.
24. **META24** With regard to META22, the LPA SHALL ignore fields it does not support.
25. **META25** The information defined in META22 SHALL NOT impact the functionalities and Profile Management Operations defined in this specification that are not Vendor specific.
26. **META26** The information defined in META22 SHALL NOT impact the interoperability of the solution defined in this specification (incl. Devices, Profiles and SMDP+).
27. **META27** With regard to META22, the eUICC SHALL store the additional proprietary information in its memory if indicated by the Profile Owner.
