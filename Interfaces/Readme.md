## Interface Definitions

1. **ES2+ `{ Operator ←→ SM-DP+ }`**
The ES2+ interface is used by the Operator to order Profiles for specific eUICCs as well as other administrative functions.
2. **ESeu `{ End User ←→ LUI }`**
ESeu is the interface between the End User and the LUI. The ESeu interface is used to support the following requirements:
    1. ESeu1
    2. ESeu2 → All Local Profile Management Operations of the LPA defined in Section SHALL be explicitly initiated or authorised by the End User or Device owner.
    3. ESeu3 → All Local Profile Management Operations of the LPA defined in Section SHALL be explicitly initiated or authorised by the End User or Device owner.
3. **ES6 `{ Operator ←→ eUICC }`** 
ES6 interface is used by the Operator for management of Operator services via OTA updates.
4. **ES9+ `{ SM-DP+ ←→ LPD }`**
The ES9+ interface facilitates secure communication between SM-DP+ and LPD, ensuring the secure transmission of the Bound Profile Package (the mobile network operator profile) from the SM-DP+ to the eUICC in the target device. This interface also supports Remote Profile Management (RPM) and Remote Enablement/Management (ReM).
5. **ES8+ `{ SM-DP+ ←→ eUICC }`**   
The ES8+ interface provides a secure channel between eUICC and SM-DP+ to administer the ISD-P along with it’s associated Profile during download and installation.
6. **ES12 `{ SM-DP+ ←→ SM-DS }`**
The ES12 interface allows SM-DP+ to register and delete it’s Event Records with SM-DS service.
7. **ES11 `{ LDS ←→ SM-DS }`**
The ES11 interface allows the LDS to retrieve Event Records for respective eUICC.
8. **ESeum `{ EUM ←→ eUICC }`**
ESeum interface is responsible for transmitting bootstrap credentials and other initialization data from the EUM to eUICC. The bootstrap profile is the default profile provided by the EUM to facilitate MNO Profile downloads from the SM-DP+ servers.
9. **ES10a `{ LDS ←→ LPA Services }`** 
The ES10a interface allows LPA to get configured addresses from the eUICC or root SM-DS and optionally the default SM-DP+ server.
10. **ES10b `{ LPD ←→ LPA Services }`**
The ES10b interface is used by LPD and LPA services to transfer a Bound Profile Package to the eUICC.
11. **ES10c `{ LUI ←→ LPA Services }`**
The ES10c interface is used
    1. between LUI and LPA services for Local Profile Management by end user.
    2. between LPR and LPA services to retrieve Metadata needed for Profile content management through LPA Proxy.
12. **ES15 `{ SM-DS ←→ SM-DS }`**
For deployments with cascaded SM-DSs, ES15 interfaces is used to connect the SM-DS servers.
13. **Established Connection `{ Device ←→ SM-DP+ }`**
Connectivity to SM-DP+ is provided by either of two ways
    1. An internet connection available or provided on the same device as LPA
    2. An internet connection shared from another device via local in-between connection
14. **ES20 `{ (D)PCMP ←→ LPR }`**
Used by PCMP or DPCMP to manage Profile contents using LPA as a proxy.
15. **ES25 `{ LUI in eUICC ←→ UIMe }`**
The ES25 interface transfers end-user related interactions between LUI in eUICC and the UIMe. The interface one of the given options
    1. LUI uses CAT commands as defined in ETSI TS 102 223 and UIMe becomes the CAT interpreter.
    2. The LUI uses SCWS as defined by OMA SpecWorks and the UIMe is a browser.
    3. The LUI uses a limited set of CAT Envelopes and UIMe is a custom application.
    4. The requirement **ES25 REQ1** applies for ES25 interface:
    → If the LUI in the eUICC uses specific CAT envelopes defined in SGP.22, then UIMe SHALL fulfil the requirements related to the LUI.
16. **ES21 `{ Device Application ←→ LPA }`**
The ES21 interface is used to trigger a Profile content management session between a (D)PCMP and a Profile from the Device Application, or to send Notifications to Device Application.
17. **ES22 `{ Device Application ←→ LPA }`**
18. **ESaa `{ LPR ←→ eUICC }`**
The ESaa interface is used for Profile content management through LPA by using it as a proxy.
19. **ESosup `{ eUICC ←→ eUICC OS Manager }`**
The ESosup interface is used to deliver eUICC OS update commands to the eUICC module.
20. **ESoem `{ OEM ←→ eUICC OS Manager }`**
This interface can be used to receive the eUICC OS Update package(s) from the OEM and to dispatch it to the eUICC OS Manager in charge of the eUICC OS Update.
21. **ESapp `{ Device Application ←→ Operator }`**
The exchanges on this interface are triggered by the Device Application. GSMA PRD Specification TS.43 is an example of protocol to use on ESapp interface.
22. **Esci `{ CI ←→ SM-DP+/SM-DS/EUM }`**
The Esci interface allows SM-DP+, SM-DS and EUM to request a certificate from CI and to retrieve certificate revocation status.
