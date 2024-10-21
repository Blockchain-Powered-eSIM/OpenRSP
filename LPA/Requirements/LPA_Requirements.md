# Local Profile Assistant (LPA) Requirements

| Requirement Number | Description |
| --- | --- |
| LPA1 | [Void] |
| LPA2 | [Void] |
| LPA3 | Security between the LUI and the associated display or input applications on the Device SHALL be provided according to current industry best practices. |
| LPA4 | Access to the LUI SHALL be protected according to current industry best practices. |
| LPA5 | All Local Profile Management Operations SHALL require User Intent except where otherwise noted in this specification. |
| LPA6 | [Void] |
| LPA7 | [Void] |
| LPA8 | The LPA SHALL protect Profile Metadata from unauthorised access.  |
| LPA9 | The Local Profile Management Operation, ‘enable’ SHALL be supported. This operation SHALL allow the End User to select the Profile to be enabled. |
| LPA10 | The Local Profile Management Operation, ‘disable’ SHALL be supported. |
| LPA11 | The Local Profile Management Operation, ‘delete’ SHALL be supported. This operation SHALL allow the End User to delete a Disabled Profile from the eUICC. The End User SHALL acknowledge the message of consequences for the deletion of the Profile. Strong Confirmation SHALL be enforced. |
| LPA12 | The Local Profile Management Operation ‘query’ SHALL be supported. This operation SHALL allow the End User to view the list of installed Operational Profiles on the eUICC and relevant associated information through the Profile Metadata. |
| LPA13 | The Local Profile Management Operation, ‘edit default SM-DP+ address’ SHOULD be supported. When supported, this operation SHALL allow the End User to edit a default SM-DP+ address. Simple confirmation SHALL be enforced. If the LPA does not support 'edit default SM-DP+ address', alternative vendor-specific methods to edit a default SM-DP+ address SHALL be provided to the End User. |
| LPA14 | The Local Profile Management Operation ‘eUICC Memory Reset’ SHALL be supported. This operation SHALL execute the eUICC Memory Reset. The End User SHALL acknowledge the message of consequences of ‘eUICC Memory Reset’. Strong Confirmation SHALL be enforced. |
| LPA15 | The Local Profile Management Operation ‘eUICC Test Memory Reset’ SHALL execute the eUICC Test Memory Reset. Simple Confirmation SHALL be enforced. |
| LPA16 | The Local Profile Management Operation ‘set/edit nickname’ SHOULD be supported. When supported, this operation SHALL allow the End User to add or modify a nickname for the selected Profile. The operation SHALL NOT modify the Mobile Service Provider name. If the LPA does not support ‘set/edit nickname’, alternative vendor-specific methods to distinguish Profiles on the LUI SHOULD be provided by the LPA. |
| LPA16a | The Local Profile Management Operation ‘add Profile via Default SM-DP+’ SHALL be supported and available to the End User if a Default SM-DP+ is populated. This operation SHALL allow the LPA to download and install a new Profile to the eUICC using the Default SM-DP+ address(es) configured on the eUICC or the Device.<br>Simple Confirmation SHALL be enforced.<br>Note: The presentation of Profile management operations to the End User on the LUI is OEM specific. For example two Profile management operations could be combined within one menu item.    |
| LPA17 | The Local Profile Management Operation ‘add Profile’ SHALL be supported. This operation SHALL allow the LPA to download and install a new Profile to the eUICC.At least these mechanisms SHALL be supported by the LPA depending on the type of Device where technically capable:<ul><li>Profile download from default SM-DP+</li><li>Profile download via SM-DS service discovery</li><li>Profile download with Activation Code</li></ul>Simple Confirmation SHALL be enforced. |
| LPA17a | An LPA with an LDS SHALL support the Local Profile Management Operation ‘add Profile via SM-DS’ and make it available to the End User. <br>Note: The presentation of Profile management operations to the End User on the LUI is OEM specific. For example, two Profile management operations could be combined within one menu item.    |
| LPA17b | Operation in LPA17 SHALL allow the LPA to download and install a new Profile to the eUICC by contacting a Root SM-DS fetched by the LPA to retrieve pending events.<br>Simple Confirmation SHALL be enforced. |
| LPA17c | The Local Profile Management Operation ‘add Profile via Activation Code’ SHALL be supported and available to the End User. This operation SHALL allow the LPA to download and install a new Profile to the eUICC with the use of an Activation Code.<br>Simple Confirmation SHALL be enforced.<br>Note: The presentation of Profile management operations to the End User on the LUI is OEM specific. For example, two Profile management operations could be combined within one menu item. |
| LPA17d | If RPM is supported by the LPA and the eUICC: the Local Profile Management Operation ’update Profile’ SHOULD be supported and available to the End User. This operation SHALL trigger Event retrieval(s) from the Polling Address (Managing SM-DP+/SM-DS address) stored in the selected Profile to retrieve RPM operations for this specific Profile.<br>Note: The presentation of Profile management operations to the End User on the LUI is OEM specific. For example, two Profile management operations could be combined within one menu item. |
| LPA18 | [Void] |
| LPA19 | [Void] |
| LPA20 | [Void] |
| LPA21 | [Void] |
| LPA22 | [Void] |
| LPA23 | [Void] |
| LPA24 | [Void] |
| LPA25 | [Void] |
| LPA26 | [Void] |
| LPA27 | When enforced, any Confirmation Request SHALL allow the End User to cancel the Local Profile Management Operation. |
| LPA28 | It SHALL be possible to expose the LUI of a Companion Device allowing input from an End User interface on the Primary Device. |
| LPA29 | [Void] |
| LPA30 | [Void] |
| LPA31 | A point-to-point secure link initiated by the End User and offering confidentiality and integrity SHALL be established between the Companion and Primary Device for any input executed from the Primary Device.  |
| LPA32 | [Void] |
| LPA33 | The Device Manufacturer of the Companion Device SHALL implement a secure measure to ensure integrity and eligibility of any application accessing the LUI. |
| LPA34 | [Void] |
| LPA35 | The LPA SHALL be able to utilise any on-Device and existing connection to the internet, such as Wi-Fi or Wi-Fi direct, in order to reach out to the SM-DP+. Over such connection, ES8+ and ES9+ interfaces can be established. |
| LPA36 | The LPA SHALL be able to utilise any internet connection offered by another Device, via other connectivity mechanisms such as cabled tethering, locally shared Wi-Fi connections or Bluetooth in order to reach out to the SM-DP+. Over such connection, ES8+, and ES9+ interfaces can be established.  |
| LPA37 | The LPA SHALL be able to determine if connectivity to the SM-DP+ is available by any means. |
| LPA38 | The LPA SHALL be able to notify the End User that there is no connection to the internet and or no connection to the SM-DP+ in order to allow the End User to enable or troubleshoot required connectivity. |
| LPA39 | [Void] |
| LPA40 | There SHALL be at most one active LPA per eUICC. |
| LPA41 | [Void] |
| LPA42 | [Void] |
| LPA43 | [Void] |
| LPA44 | The LPA SHALL be able to read the Profile Policy Rules.  |
| LPA45 | [Void] |
| LPA46 | Prior to downloading a new Profile, the LPA SHALL check the condition for whether the Enabled Profile, if any, has enabled POL RULE1. If this is the case, a dedicated message SHALL be displayed identifying the consequences to the End User. Examples of information that may be displayed would be:<ul><li>Enabling of the new Profile will not be possible because the currently Enabled Profile cannot be disabled.<\li><li>The Profile name of the Enabled Profile.</li><li>For more information, the End User should contact the Profile Owner of this Profile.</li></ul>With displaying this message, the End User SHALL be able to decide on whether to continue the download or to cancel the operation. This dialogue MAY be combined with the regular User Intent for confirming a Profile download. |
| LPA47 | The communication between the End User interface of the Primary Device and the LUI of the Companion Device SHALL be protected (confidentiality, integrity and authentication). |
| LPA48 | [Void] |
| LPA49 | Confirmation Requests for consecutive Local Profile Management Operations MAY be achieved in one step as long as the different actions of the separate operations are clearly explained and offered to the End User. For instance, upon installation of a new Profile, the LPA MAY propose ‘add Profile’ and ‘enable’ into one single step with a single confirmation only (e.g. “Do you want to install Profile ‘ProfileName’ on your Device and enable it? Yes / No / Install only”)  |
| LPA50 | When consecutive operations are achieved in one single step (LPA49), the highest level of confirmation SHALL be applied - i.e. in the case of two operations having respectively Strong and Simple Confirmation Requests, the single step SHALL use the Strong Confirmation Request.  |
| LPA51 | The Local Profile Management Operations ‘enable’ (LPA9), ‘disable’ (LPA10), and ‘delete’ (LPA11) SHALL be able to trigger a Notification to the Notification Receivers of the respective Profile being managed to indicate that this operation was actioned. These Notifications are sent on a best effort basis and SHALL NOT impact otherwise the operation. |
| LPA52 | The LPA SHALL provide a Trusted Link from the End User to the eUICC through the LUI. |
| LPA53 | The End User SHOULD be able to configure the LPA such that the automatic Event Record retrieval from the SM-DS is disabled. |
| LPA54 | The LPA SHALL be able to read any SM-DS and SM-DP+ addresses configured in the eUICC.  |
| LPA55 | [Void] |
| LPA56 | LPA Integrity SHALL be ensured using the best practice methods on the targeted platform. See Annex G.  |
| LPA57 | The polling mechanism in the LPA SHALL have two types of triggers; those that are event based, and those that are End User initiated. |
| LPA58 | Event based triggers for polling SHOULD include Device power-up when no Operational Profile is installed; in addition other triggers MAY be provided. Event based triggers MAY be disabled by the End User. |
| LPA59 | [Void] |
| LPA60 | [Void] |
| LPA61 | Error/retry handling of the LPA polling mechanism SHOULD be implemented e.g. advise the End User to retry or automatically retry as appropriate. The corresponding confirmation needs to be enforced in the retry cases. |
| LPA62 | As part of the initial Device setup, if no Operational Profile is already installed, means SHALL be provided to the End User to retrieve pending Profiles. This includes means such as checking for pending Profiles from Default SM-DP(s)+ if configured, pending profiles registered to Root/Alternative SM-DS(s), and/or using Activation Codes provided by the Mobile Service Provider.<br>Simple Confirmation is required.<br>Note: This is implementation dependent and retrieval does not need to happen exactly during the initial Device setup if the End User, as an example, is informed on how to retrieve these Profiles after the setup. |
| LPA63 | The End User SHALL always be able to manually request the retrieval of any waiting Event Record via the LPA if there are no default SM-DP+ addresses.Note: This may be achieved through the combination with existing operations – e.g. pressing “add Profile” would contact the server to retrieve an Event. |
| LPA64 | The Mobile Service Provider name SHALL be given in the signalling information from the SM-DP+ to the LPA when initiating the download of a Profile and shown to the End User before the Profile is downloaded.Simple Confirmation SHALL be enforced. |
| LPA65 | [Void] |
| LPA66 | [Void] |
| LPA67 | If the SM-DP+ stops the Profile download procedure, the LPA SHALL notify the End User. |
| LPA68 | [Void] |
| LPA69 | As part of the process of downloading a new Profile, the LPA SHOULD offer the choice to the End User to enable or not enable the new Profile. |
| LPA70 | The LUI SHOULD provide a local configuration option that allows the End User to turn on/off RPM operations. |
| LPA71 | The LPA MAY provide a means by which the eUICC can request the LPA to check for Events or pending RSP operations as described by EUICC55 and EUICC56. |
| LPA72 | An LPA with an LDS SHALL retrieve one or more Root SM-DS addresses, either stored on the eUICC or stored within the Device. |
| LPA73 | It SHALL NOT be required for the LPA to maintain state for any transactions from the SM-DS(s) except the cascade Event Retrieval(s). |
