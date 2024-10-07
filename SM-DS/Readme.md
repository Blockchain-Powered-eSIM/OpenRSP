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

## Event Registration/Deletion Procedure
The procedure for a deployment with the Root SM-DS and an Alternative SM-DS (cascade mode).

<img width="600" alt="Screenshot 2024-10-07 at 4 19 55 PM" src="https://github.com/user-attachments/assets/04cecc7c-5f19-45e0-a411-40fbfcef7ea8">

### Event Registration Procedure  

**Starting Condition:**  
a. The SM-DP+ has an Event Registration action waiting for a target eUICC identified by the EID.  

#### Procedure:  
1. The SM-DP+ establishes a secure connection to an Alternative SM-DS of the Profile Owner´s choice.
2. The SM-DP+ notifies the Alternative SM-DS about an Event Registration action.
3. to 4. The Alternative SM-DS registers and confirms the Event Registration.
5. The Alternative SM-DS establishes a secure connection to the Root SM-DS.
6. The Alternative SM-DS informs the Root SM-DS that for the given EID, an Event Record is waiting at the Alternative SM-DS.
7. The Root SM-DS registers the Event Registration.
8. The Root SM-DS confirms the receipt of the information.

### Event Deletion Procedure:

**Starting Condition**
a. The SM-DP+ has an Event Deletion action waiting for a target eUICC identified by the EID.

#### Procedure:  
1. The SM-DP+ establishes a secure connection to an Alternative SM-DS of the Profile Owner´s choice.
2. The SM-DP+ notifies the Alternative SM-DS about an Event Deletion action.
3. to 4. The Alternative SM-DS deletes the Event Record and confirms the Event Deletion.
5. The Alternative SM-DS establishes a secure connection to the Root SM-DS.
6. The Alternative SM-DS informs the Root SM-DS that for the given EID, an Event Record has to be deleted.
7. The Root SM-DS deletes the Event Record.
8. The Root SM-DS confirms the deletion of the Event Record.

## Discovery Request Procedure  
The procedure for a deployment with an Alternative SM-DS and the Root SM-DS (cascade mode).

<img width="616" alt="Screenshot 2024-10-07 at 4 26 19 PM" src="https://github.com/user-attachments/assets/c3ec989a-ce56-42eb-8bc4-de1abb0665eb">

### Procedure:

1. to 3. In order to generate a Discovery Request, the LDS requests the eUICC to generate its Authentication information which contains (at least) the eUICC-Certificate and is signed by the eUICC.
4. to 5. The LDS establishes a secure communication to the Root SM-DS.
6. The Root SM-DS verifies the authenticity of the eUICC by checking the eUICC Authentication information.
7. If the eUICC is authentic and an Event Record is waiting, the Root SM-DS delivers back:
    - **Option a**: The address of the SM-DP+ where an action is waiting.
    - **Option b**: The rest of the following actions:
        1. The address of the Alternative SM-DS, where an Event Record can be retrieved.
        2. The LDS establishes a secure connection to the Alternative SM-DS.
        3. The Alternative SM-DS verifies the authenticity of the eUICC by checking the eUICC Authentication information.
        4. If the eUICC is authentic and an Event Record has been received, the Alternative SM-DS delivers back the address of the SM-DP+ where an action is waiting.
8. The LPA establishes a connection to the SM-DP+ and the waiting action can be performed.
