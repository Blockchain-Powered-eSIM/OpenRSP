## LPA API Access Control Requirements

| Requirement Number | Description |
| --- | --- |
| LPAAPIAC1 | A Device supporting an LPA API SHALL provide a mechanism which can authorise applications’ access to LPA API.  |
| LPAAPIAC2 | The Device MAY refer to GP SEAC or GP DAC to implement the LPA API access control mechanism. |

## Application Protocol Data Unit (APDU) Access API Requirements

| Requirement Number | Description |
| --- | --- |
| APDUAPI1 | A Device MAY support the APDU Access API requirements in this section. NFC Devices SHALL support the APDU Access API requirements in this section. |
| APDUAPI2 | If the Device supports APDU Access API as per requirement APDUAPI1, the Device SHALL provide a mechanism by which authorised applications can send APDUs to the Enabled Profile. |
| APDUAPI3 | The Device SHALL authorise applications by retrieving and enforcing Access Rules of the corresponding Profile as specified in the GlobalPlatform SEAC specification |
| APDUAPI4 | The Access Rules for the Enabled Profile SHALL be stored as part of the Profile. |
| APDUAPI5 | Within the Enabled Profile only the contents of the Profile itself SHALL be accessible to authorised applications. |
