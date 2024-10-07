# Subscription Manager – Discovery Service (SM-DS)

## Overview
The role of the SM-DS is to,  
- Provide mechanisms that allow an SM-DP+ to inform the LDS within any Device that an SM-DP+ wishes to communicate with it.
- The purpose of the SMDS to LDS communication SHALL be informing the LDS of a pending Event.

The principle of operation remains the same for all use cases,  
_**The SM-DP+ will send an Event Registration message for a target Device to an SM-DS.**_  
In a simple deployment, only the Root SM-DS is configured on the eUICC.
- The Root SM-DS address is unique and filled in the eUICC.
- The LDS in the target Device polls the Root SM-DS using the same logical location.
- When the Root SM-DS has an Event-ID for the target Device it will respond with the SM-DP+ address, or
- If there is no Event-ID the response will be a null response.

In a deployment with cascaded SM-DSs, the SM-DP+ will send an Event Registration to an,
- Alternative SM-DS, which may not be configured as the Root SM-DS on the eUICC.
- This alternative SM-DS will cascade the Event Registration to the Root SM-DS.
- The LDS in the target Device polls the Root SM-DS and will receive the Alternative SM-DS address.
- It will then request the Event from the Alternative SM-DS, which will respond with the SM-DP+ address.

<img width="578" alt="Screenshot 2024-10-07 at 4 07 13 PM" src="https://github.com/user-attachments/assets/2d5562ad-8ddc-4ca2-8437-36a067339389">

## Implementation
Two configurations of the SM-DS MAY exist:
• A Root SM-DS
• An Alternative SM-DS

**The Root SM-DS is configured at the time of Device manufacture and is invariant.**
<img width="595" alt="Screenshot 2024-10-07 at 4 09 07 PM" src="https://github.com/user-attachments/assets/ab654526-2c00-4ab4-bc1e-6ca7f2f1de37">

## Implementation Guidelines:
The following statements SHOULD be considered when defining a technical implementation:
- A competitive environment on the supply of SM-DS services SHOULD be favoured by the approach.
- There SHOULD be no single-points-of-failure.
- Implementation SHOULD inherently provide both vertical and horizontal performance/scalability.
- There SHOULD be no need for pre-registration of Devices or eUICCs at a certain SM-DS.

## Functions

### Event Registration 
Process by which an Event Record received from an SM-DP+ is stored.

### Event Deletion
Process by which an SM-DP+ can delete its own Event Record.

### Event Checking
Provides the presence of registered Event Records, upon Event Checking request from any enquiring LDS.

### Event Retrieval
Provides all registered Event Records, upon Discovery Request from any enquiring LDS.
