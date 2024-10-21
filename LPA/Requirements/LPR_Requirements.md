# LPA Proxy Requirements

| Requirement Number | Description |
| --- | --- |
| LPAPR1 | It is OPTIONAL for the Device, the eUICC, and the SM-DP+ to support the LPA Proxy requirements defined in this document. |
| LPAPR2 | The LPR SHALL be able to forward APDUs remotely sent from a Profile Content Management Platform or from a Delegated Profile Content Management Platform to any application on the Enabled Profile.<br>Note: The mechanism cannot address a Disabled Profile |
| LPAPR3 | A mechanism allowing the LPR to connect to a Profile Content Management Platform address, each time the Profile is Enabled, SHALL exist. This mechanism SHALL be executed on a best effort basis and SHALL NOT impact otherwise the pending RSP operations. |
| LPAPR4 | The DPI used for redirection from a PCMP to a DPCMP, SHALL be able to be included in the Profile. |
| LPAPR5 | The Profile Content Management Platform address and the configuration (LPAPR3/deactivated) of the mechanism described in LPAPR3 SHALL be included in the Profile.  |
| LPAPR6 | The mechanism described in LPAPR3 SHALL be activated/deactivated by the Profile Owner.  |
| LPAPR7 | It SHALL be possible for the PCMP to request redirects to some Delegated Profile Content Management Platform(s). A redirection MAY happen at any point of time during the data exchange between the PCMP and the LPR. The PCMP internal routing logic MAY use the DPI parameter, if provided, the ICCID and any other contextual data. |
| LPAPR8 | The identifier parameter for the routing to a Delegated Profile Content Management Platform, called the DPI, SHALL be globally unique.  |
| LPAPR9 | The protocol used between the LPR and its Profile Content Management Platform SHALL be able to transport all types of SCP designed to address the Enabled Profile through logical channels. E.g. this may include SCP03 and SCP11. |
| LPAPR10 | When triggered, the LPR SHALL connect to the PCMP address retrieved from the Enabled Profile. If the triggering method includes a DPI as a parameter, this parameter SHALL be added to the PCMP address. If a DPI parameter is filled in the Enabled Profile, this parameter SHALL also be added to the PCMP address. |
| LPAPR11 | The capability to use mobile network data for the LPA Proxy MAY be enabled/disabled by the End User.<br>The Default state SHALL be ‘enabled’. |
| LPAPR12 | The Device SHALL provide a means to Device Application to interact with LPA Proxy through this API. The requirements about this API are detailed in LPAPR13 to LPAPR17. |
| LPAPR13 | The access to the LPA Proxy API by a Device Application SHALL be authorised by the Profile Owner of the Enabled Profile. |
| LPAPR14 | The Device SHALL offer a means for Device Applications to detect whether the LPA Proxy is deployed on the Device or not. |
| LPAPR15 | A triggering Device Application SHALL be able to register interest for receiving Notifications during the triggered session. |
| LPAPR16 | The LPA Proxy SHALL be able to send Notifications to the triggering Device Application. These Notifications SHALL either<br><ul><li>be contained in the command sequence retrieved from the Profile Content Management Platform (e.g. for task overview message, initialisation or end of the process)</li><li>or generated locally (e.g. error Notifications)</li></ul> |
| LPAPR17 | The LPA SHOULD provide a mechanism to allow a Device Application to get progress or result information about an LPA Proxy operation which it requested through an API. |
