# Profile Policy Management

The Profile Policy Management function enables Mobile Service Providers to implement mechanisms that enforce the conditions or policies—both operational and business—under which services are offered to Subscribers. In certain cases, this MAY also involve enforcing policies defined by the Subscriber.  
Profile Policy Management MAY be integrated with other existing Policy Enforcement technologies, contingent on agreements made with the Subscriber.  
This function is realised through two essential components. The first is the Profile Policy Enabler, which resides in the eUICC. The second component consists of a defined set of Profile Policy Rules necessary for enforcing specific policies.  
Requirements for Profile Policy Management can be referred [here](./Requirements/Profile_policy_requirements.md)
The following Policy Rules also apply to Profile Policy Management

| Policy Number | Description |
| --- | --- |
| POL RULE1 | The Profile Policy Rule ‘Disabling of this Profile is not allowed’ SHALL only
be supported by non MEP-capable eUICCs. |
| POL RULE2 | The Profile Policy Rule ‘Deletion of this Profile is not allowed’ SHALL be
supported |

## Profile Policy Enabler

The Rules Authorisation Table (RAT) defines the Profile Policy Rules (PPR) that can be set in a Profile intended for installation on the eUICC. The RAT is established at the eUICC platform level and is utilised by both the Profile Policy Enabler (PPE) and the LPA to assess whether a Profile containing PPRs is authorised for installation on the eUICC.  
The RAT is either provisioned during the eUICC’s manufacturing or during the initial Device setup, assuming no Operational Profile is already installed. The responsibility for configuring the RAT content lies with the OEM or EUM.  
The RAT may include the following:

- A collection of entries allowing the use of specific Profile Policy Rules.
- Operator-specific entries providing exceptions to the requirement for Strong Confirmation before downloading and installing a Profile that contains particular Profile Policy Rules.

Requirements for Profile Policy Enabler can be referred [here](./Requirements/Profile_requirements.md)
