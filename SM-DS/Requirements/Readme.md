# SM-DS Requirements

## SMDS1
The SM-DS SHALL enable an LDS to discover its own Event Records registered by SM-DP+(s) or by Alternative SM-DS(s).

## SMDS2
**[Void]**

## SMDS3
All Discovery Requests and Event Registrations SHALL be processed by any Root SM-DS in a non-discriminatory manner.

## SMDS4
The SM-DS SHALL accept Event Registrations from:
- any authorised and authenticated SM-DP+(s) having a valid Certificate.
- any authorised and authenticated SM-DS(s) having a valid Certificate.

## SMDS5
The SM-DS SHALL only accept Discovery Requests authenticated by the eUICC via the corresponding LDS.

## SMDS6
The SM-DS and the SM-DP+ as well as connected SM-DSs SHALL be mutually authenticated.

## SMDS7
The SM-DS SHALL NOT have visibility of any data that may be used to compromise the End User’s privacy.

## SMDS8
The SM-DS SHALL support multiple concurrent Event Registrations per eUICC and SHALL present to the LDS all currently valid Event Records in the same order as they were received by the SM-DS (first in, first out).

### SMDS8a
As per SMDS8, the valid Event Records SHALL be filtered by the RSP operation type provided by the LDS (if any).

## SMDS9
The SM-DS SHOULD protect itself to avoid becoming a point of injection for DoS or spam attacks.

## SMDS10
Subscriber Specific data and Profile related contents SHALL NOT be stored within the SM-DS.

## SMDS11
The SM-DS SHALL NOT allow the harvesting of any information such as Mobile Service Provider, Operator, EIDs, Device Manufacturers, Devices, etc.

## SMDS12
The SM-DS SHALL only return to the LDS the Event Records related to the served eUICC.

## SMDS13
The SM-DS SHALL NOT have any contact with the Profile Packages, e.g., SHALL NOT store or process any Profile Package, or RPM commands.

## SMDS14
The SM-DS SHALL provide the same data regardless of the status of the Device that queries it (i.e., consistent in time and in geographic location).

## SMDS15
The SM-DS SHOULD NOT significantly impact the end-to-end provisioning time.

## SMDS16
The SM-DS SHALL provide defence against Denial of Service attacks.

## SMDS17
All communications to, from, and between entities of the SM-DS SHALL be encrypted and integrity protected.

## SMDS18
The SM-DP+ SHALL be able to delete any of its own Event Records registered on the SM-DS.

## SMDS19
An Alternative SM-DS SHALL be able to delete any of its own Event Records registered on the Root SM-DS (in response to an SM-DP+ delete operation defined in SMDS18).

## SMDS20
An Alternative SM-DS SHALL propagate the Event Record to the Root SM-DS if requested by the SM-DP+.

## SMDS21
If there are multiple Event Records registered on the SM-DS for one eUICC, these SHALL all be sent as a single response unless the discovery operation requests a specific event to be returned, in which case only that Event SHALL be sent.

## SMDS22
An SM-DP+ SHALL be able to send an Event Record to an LDS either by a Root SM-DS or via any Alternative SM-DS selected by the SM-DP+. If an Alternative SM-DS is selected, the Event Record to the LDS SHALL come from this Alternative SM-DS.

## SMDS23
**[Void]**

## SMDS24
A Root SM-DS SHALL be managed by the GSMA. This Root SM-DS MAY be used as a default Root SM-DS.

## SMDS25
**(FFS) [Void]**

## SMDS26
**(FFS) [Void]**

## SMDS27
**(FFS) [Void]**

## SMDS28
**(FFS) [Void]**

## SMDS29
**(FFS) [Void]**

## SMDS30
**(FFS) [Void]**

## SMDS31
**(FFS) [Void]**

## SMDS32
The SM-DS MAY support the Event Checking procedure. If the Event Checking procedure is supported by the SM-DS, SMDS33 SHALL apply.

## SMDS33
Upon the request from an LDS for Event Checking, the SM-DS SHALL provide the information to the LDS whether it has any Event registered for the corresponding eUICC.

## SMDS34
The SM-DS MAY support none, one, or multiple kinds of Push Services available in the industry. If a Push Service is supported by the SM-DS, SMDS35 and SMDS36 SHALL apply.

## SMDS35
If requested by the LDS as per LDS8, the SM-DS SHALL return the indication whether it accepts or rejects the request.

## SMDS36
If accepted by the SM-DS as per SMDS35, the SM-DS SHALL notify the LDS about the Event Registration using the Push Service, whenever an Event is newly registered for the eUICC.
