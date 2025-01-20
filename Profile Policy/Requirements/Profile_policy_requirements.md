## Profile Policy Management Requirements

| Requirement Number | Description |
| --- | --- |
| POL1 | A Profile Policy Rule SHALL only be configured within a Profile. |
| POL2 | Each Profile MAY have Profile Policy Rules associated to itself. |
| POL3 | A Profile Policy Rule SHALL only apply to the Profile that contains it. |
| POL4 | [Void] |
| POL5 | Profile Policy Enforcement SHALL be able to resolve any Profile Policy Rule conflict.  |
| POL6 | The updating of a Profile’s Policy Rules SHALL be restricted to the Profile Owner.  |
| POL7 | The mechanism used for the update of a Profile Policy Rule SHALL be atomic. |
| POL8 | The set of Profile Policy Rules SHALL be extensible for future releases.  |
| POL9 | [Void] |
| POL10 | A Profile Policy Rule SHALL be enforced whenever a Profile state change is attempted. |
| POL11 | Downloading and installing a Profile in a non-MEP-capable eUICC with theProfile Policy Rule ‘Disabling of this Profile is not allowed’ (POL RULE1) SHALL only be possible if no other Operational Profile is currently installed. |
| POL11a | Downloading and installing a Profile with the POL RULE1 in an MEP-capable eUICC SHALL NOT be allowed. |
| POL12 | The LPA and the eUICC SHALL prevent the downloading and installation of a Profile containing Profile Policy Rules that conflict with the Profile Policy Rules of the already installed Profiles. |
| POL13 | A Profile Owner SHALL be able to unset the Profile Policy Rules of its Profile using the ES6 interface. |
| POL13a | If RPM is supported by the Managing SM-DP+, the LPA and the eUICC: a Profile Owner SHALL be able to unset the Profile Policy Rules of its Profile via a Managing SM-DP+ using the ES9+ interface.<br>**NOTE**: The setting of Profile Policy Rules on the ES9+ interface is a potential feature for a future release.    |
| POL14 | Before a Profile is installed with Profile Policy Rules, the End User SHALL be able to be notified if needed about the Profile Policy Rules and if notified, the installation SHALL thereafter be conditional on End User Strong Confirmation. |
| POL15 | The request for End User consent for the installation of Profile Policy Rules and Profile download MAY be combined into a single prompt therefore requiring a single confirmation by the End User. |
| POL15a | Where End User consent is required for the download of the Profile which includes Policy Rules, the Mobile Service Provider SHALL be able to provide a message for the End User that MAY be displayed by the Device.<br>**NOTE**: Consideration should be made for the display of lengthy text on a Device with a limited display. |
| POL16 | Profile Policy Rules SHALL be enforced by the Profile Policy Enabler in the eUICC. |
| POL17 | The Profile Policy Enabler SHALL only support the Profile Policy Rules defined in this specification. |
| POL18 | The Profile Policy Enabler SHALL be capable of supporting all the Profile Policy Rules as defined in this specification.  |
| POL19  | [Void] |
| POL20 | Allowing the installation of a Profile with Profile Policy Rules SHALL be subject to compliance with local regulatory requirements. |
| POL21 | Profile Policy Rules MAY be configured for Profiles only if the Profile Owner can be identified in the Metadata.<br>**NOTE**: POLPPE requirements depend on the identification of the Profile Owner. |
