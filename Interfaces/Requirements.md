This documents lists the general interface requirements for eUICC and LPA interfaces as per [GSMA RSP SGP.21](https://www.gsma.com/solutions-and-impact/technologies/esim/wp-content/uploads/2023/12/SGP.21-V3.1.pdf) document.

1. INT1 - All interfaces from the eUICC SHALL indicate the eSVN.
2. INT2 - The behaviour of all interfaces SHALL support the indicated eSVN.
3. INT3 - The SM-DP+ and SM-DS SHALL use the capabilities indicated by the eUICC to determine its response to the eUICC.
4. INT4 - All communicating entities involved in Remote SIM Provisioning SHALL be mutually authenticated. The Device and the eUICC are considered as one entity in this context.
5. ESeu2 - All Local Profile Management Operations of the LPA SHALL be explicitly initiated or authorised by the End User or Device owner.
6. ESeu3 - The ESeu interface SHALL support the triggering and confirmation of the Profile download and installation operation and Local Profile Management Operations requested by the End User.
7. ES25 REQ1 - If the LUI in the eUICC uses specific CAT Envelopes defined in SGP.22, then the UIMe SHALL fulfil the requirements related to the LUI.
