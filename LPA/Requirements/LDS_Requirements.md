# Local Discovery Services (LDS) Requirements

| Requirement Number | Description |
| --- | --- |
| LDS1 | The LDS SHALL be able to read out the root SM-DS address configured in the eUICC and the Alternative SM-DS address configured in the installed Profiles. |
| LDS2 | The LDS MAY support the Event Checking procedure. If the Event Checking procedure is supported by the LDS, requirements LDS3 to LDS6 SHALL apply. |
| LDS3 | The Event Checking procedure SHALL provide a means for the LDS to query the SM-DS to determine the presence of any Event Records registered for an eUICC, without requiring the eUICC and SM-DS to perform the common mutual authentication procedure. |
| LDS4 | During the Event Checking procedure, the LDS SHALL provide the SM-DS an information for identifying the eUICC in order to check the presence of Event Record(s) registered for that eUICC, without compromising the privacy of the EID. |
| LDS5 | There SHALL be a means for the LDS to determine whether the SM-DS supports the Event Checking (e.g. by a pre-configuration by the OEM or by a response from the SM-DS). |
| LDS6 | If both the LDS and the SM-DS support Event Checking, the LDS SHOULD perform the Event Checking procedure prior to the Event Retrieval against that SM-DS. |
| LDS7 | The LDS MAY support a Push Service. If a Push Service is supported by the LDS, requirements LDS8 and LDS9 SHALL apply. |
| LDS8 | There SHALL be a means for the LDS to request an SM-DS to be notified about Events registered for the eUICC. |
| LDS9 | With regard to LDS8, the request SHALL include the information for identifying the corresponding eUICC and the information about the Push Service to be used by the SM-DS for the notification. |
