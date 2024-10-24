## Profile Metadata Requirements

| Requirement Number | Description |
| --- | --- |
| META1 | All Profiles SHALL have associated Profile Metadata. |
| META2 | Unless specified otherwise in the below requirements, the Profile Metadata SHALL be stored in the eUICC.  |
| META3 | The Profile Metadata SHALL be accessible irrespective of the state of the Profile.  |
| META4 | The Profile Metadata SHALL include a field for the Mobile Service Provider name.<br>**NOTE**: EFSPN is already used in a different context outside of this specification and could be blank. |
| META5 | The Profile Metadata SHALL include a field for the ICCID of the Profile. |
| META6 | The Profile Metadata SHALL include a field for the End User nickname of the Profile. |
| META7 | The Profile Metadata SHALL include a field for containing a short description of the Profile defined by the Operator or Mobile Service Provider. |
| META8 | [Void] |
| META9 | The Profile Metadata SHALL always be available to the LPA. The display to the End User is implementation-specific. |
| META10 | The Profile Metadata SHALL include an OPTIONAL field to allow the display of an icon defined by the Operator or Mobile Service Provider for the respective Profile.  |
| META11 | The Profile Metadata SHALL be able to include a copy of the Profile Policy Rules associated to the Profile. |
| META11a | The Profile Metadata SHALL be able to include a message that is to be displayed to the End User when the Profile contains a Profile Policy Rule. It SHALL NOT be stored after Profile download. |
| META12 | All Profiles SHALL be uniquely identified in the Profile Metadata as Operational, Provisioning or Test Profile. |
| META13 | An Operator, potentially on behalf of a Mobile Service Provider SHALL be able to access and update the following Profile Metadata of its Profile using the ES6 interface if the Profile is Enabled:<br><li> Mobile Service Provider name<li> Short description of the Profile<li> Icon of the Profile<li> HR icon reference<li> List of Managing SM-DP+ and their respective authorisations to update individual Profile Metadata items<li> Profile Owner OIDs that are allowed to implicitly disable this Profile by RPM ‘Enable’<li> Polling Address<li> Profile Policy Rules (unset only)<li> Enterprise ID (access only)<li> Enterprise Name<li> Enterprise Rules<li> Device Change Configuration of the Profile<br>The content of the respective Profile SHALL reflect the updated Profile Metadata. |
| META14 | The Profile Metadata SHALL include an OPTIONAL field (named HR icon reference) that enables access to high resolution icons. The icons MAY be hosted by the SM-DP+ that handles the Profile.  |
| META15 | The HR icon reference SHALL allow the LPA to retrieve one or several icons for a Profile in the format(s) best suited for presentation on the user interface. Best fitting icons are intended to be shown during Profile download, Profile selection etc. |
| META16 | The HR icon solution SHALL provide an option to allow the HR icon(s) to be provided during the Profile download procedure. |
| META17 | The Profile Metadata SHALL include an OPTIONAL field for Device Change Configuration of the Profile. This field SHALL include OPTIONAL sub-fields for:<br><li> The address of the SM-DP+ that processes Device Change request<li> The Activation Code to be used by the new Device for Device Change<li> An indication of whether the Profile has to be deleted before the Activation Code is made available for the new Device, where the Activation Code is either from the present sub-field or what was used to trigger the original Profile Download procedure<br>**NOTE**: If an Activation Code is present in the sub-field, then it supersedes the Activation Code that was used to trigger the original Profile Download procedure. |
| META18 | The Profile Metadata SHALL be able to include an optional field for the estimated installed size of the Profile. |
| META19 | The Profile Metadata SHALL be able to include a list of Managing SM-DP+(s). |
| META20 | The Profile Metadata SHALL include an optional field to allow for the inclusion of the Enterprise ID. |
| META21 | The Profile Metadata SHALL include an optional field to allow for the inclusion of the Enterprise Name. |
| META22 | The Profile Metadata SHALL be able to include additional proprietary information. The additional proprietary information SHALL include a field for uniquely identifying the issuer of the additional proprietary information. |
| META23 | With regard to META22, the eUICC SHALL ignore fields it does not support. |
| META24 | With regard to META22, the LPA SHALL ignore fields it does not support. |
| META25 | The information defined in META22 SHALL NOT impact the functionalities and Profile Management Operations defined in this specification that are not Vendor specific. |
| META26 | The information defined in META22 SHALL NOT impact the interoperability of the solution defined in this specification (incl. Devices, Profiles and SM-DP+). |
| META27 | With regard to META22, the eUICC SHALL store the additional proprietary information in its memory if indicated by the Profile Owner |
