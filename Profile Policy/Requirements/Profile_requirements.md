## Profile Policy Enabler Requirements

| Policy Number | Description |
| --- | --- |
| POLPPE1 | The Rules Authorisation Table (RAT) SHALL be stored in the Profile Policy Enabler in the eUICC.  |
| POLPPE2 | The Profile Policy Enabler SHALL enforce the contents of the installed RAT at (and only at) Profile installation time. |
| POLPPE3 | The RAT SHALL allow multiple Profile Owners to have Profile Policy Rules enabled in their Profiles. |
| POLPPE4 | The RAT SHALL be able to support specific configurations which allow a set of, or all, Profile Policy Rules for any Profile Owner. |
| POLPPE5 | The RAT SHALL only be installed at pre-issuance or during the initial Device setup provided there are no Operational Profiles installed. |
| POLPPE6 | The RAT SHALL NOT be affected by the eUICC Memory Reset function. |
| POLPPE7 | To support identifiable regulatory requirement, a RAT SHALL be able to support a specific configuration which MAY forbid any Profile Owner to set a specific Profile Policy Rule.   |
| POLPPE8 | [Void] |
| POLPPE9 | Where the RAT allows the Profile Policy Rules for the Profile being installed, installation SHALL proceed as stated in POL14. |
| POLPPE10 | The RAT SHALL be able to support a setting to display the consequences of the Profile Policy Rules to the End User and require Strong Confirmation before the download of the Profile. |
| POLPPE11 | The OEM or EUM SHALL be responsible for provisioning the RAT into the eUICC. |
| POLPPE12 | A RAT MAY be configured in the eUICC. If the RAT is not present, the eUICC SHALL regard this as a RAT with no entry. |
