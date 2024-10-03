### All Interfaces:

- **1) ES2+ `{ Operator ⇒ SM-DP+ }`**
    
    The ES2+ interface is used by the Operator to order Profiles for specific eUICCs as well as other administrative functions.
    
- **2) ESeu `{ End User ⇒ LUI }`**
    
    ESeu is the interface between the End User and the LUI.
    The ESeu interface is used to support the following requirements:
    - **ESeu1** 
    - **ESeu2** [All Local Profile Management Operations of the LPA defined in Section SHALL be explicitly initiated or authorised by the End User or Device owner.]
    - **ESeu3** [The ESeu interface SHALL support the triggering and confirmation of the Profile download and installation operation and Local Profile Management Operations requested by the End User.]
    
- **3) ES6 `{ Operator ⇒ eUICC }`**
    
    The ES6 interface is used by the Operator for the management of Operator services via OTA services.
    
- **4) ES6 `{ Operator ⇒ eUICC }`**
    
    The ES6 interface is used by the Operator for the management of Operator services via OTA services.
    
- **5) ES8+ `{ SM-DP+ ⇒ eUICC }`**
    
    The ES8+ interface provides a secure end-to-end channel between the SM-DP+ and the eUICC for the administration of the ISD-P and the associated Profile during download and installation.
    
- **6) ES12 `{ SM-DP+ ⇒ SM-DS }`**
    
    The ES12 interface allows the SM-DP+ to register Event Records with the SM-DS and to delete its Event Records.
    
- **7) ES11 `{ LDS ⇒ SM-DS }`**
    
    The ES11 interface allows the LDS to retrieve Event Records for the respective eUICC
    
- **8) ESeum `{ EUM ⇒ eUICC }`**
    
    ESeum is the interface between the EUM and the eUICC. Out Of Scope
    
- **9) ES10a `{ LDS ⇒ LPA-Services }`**
    
    The ES10a interface is used by the LPA in the Device to get the configured addresses from the eUICC for Root SM-DS, and optionally the default SM-DP+(s).
    
- **10) ES10b `{ LPD ⇒ LPA-Services }`**
    
    The ES10b interface is used by the LPD in the Device and the LPA services to transfer a Bound Profile Package to the eUICC.
    
- **11) ES10c `{ LUI ⇒ LPA-Services }`**
    
    The ES10c interface is used
    - between the LUI in the Device and the LPA services for Local Profile Management by the End User.
    - between the LPR in the Device and the LPA services to retrieve Metadata that would be needed for Profile content management through LPA Proxy.
    
- **12) ES15 `{ SM-DS ⇒ SM-DS }`**
    
    In the case of deployments with cascaded SM-DSs, the ES15 interface is used to connect the SM-DSs.
    
---
>
>**Device – SM-DP+ (Established Connection)**
*This connection will be provided either by:
• An internet connectivity available or provided on the same Device where the LPA resides
or
• An internet connection shared from another Device via a local go-between connection*
>
>Example Connection Methods for Companion Devices to reach out to the SM-DP+
>><img width="557" alt="Screenshot 2024-10-03 at 10 40 52 PM" src="https://github.com/user-attachments/assets/3c6847fc-418e-4b30-9981-ed3efed0ae65">
>Example Connection Methods for Companion Devices to reach out to the SM-DP+ with a Remote Primary Device
>><img width="564" alt="Screenshot 2024-10-03 at 10 41 59 PM" src="https://github.com/user-attachments/assets/b391a310-1c77-418f-b480-f2cf9636f072">

>
>**General Interface Requirements**
>- **INT1** :  *All interfaces from the eUICC SHALL indicate the eSVN.*
>- **INT2** : *The behaviour of all interfaces SHALL support the indicated eSVN.*
>- **INT3** : *The SM-DP+ and SM-DS SHALL use the capabilities indicated by the eUICC to determine its response to the eUICC.*
>- **INT4** : *All communicating entities involved in Remote SIM Provisioning SHALL be mutually authenticated. The Device and the eUICC are considered as one entity in this context.*

---
- **13) ES20 `{ (D)PCMP ⇒ LPR }`**
    
    The ES20 interface is used by the PCMP or DPCMP to manage Profile contents through the use of the LPA as a proxy.
    
- **14) ES25 `{ LUI in the eUICC ⇒ UIMe }`**
    
    The ES25 interface is used between the LUI in the eUICC and the UIMe to transfer End User related interaction. This interface uses one of the following options:
  - The LUI uses CAT commands (e.g. CAT menu navigation) as defined in ETSI TS 102 223 and the UIMe is the CAT interpreter. Besides the support of these commands, there are no additional requirements for the UIMe.
  - The LUI uses SCWS as defined by OMA SpecWorks and the UIMe is a browser. Besides the support of these commands, there are no additional requirements for the UIMe.
  - The LUI uses a limited set of specific CAT Envelopes and the UIMe is a tailored application.
    
    **ES25** **REQ1** : If the LUI in the eUICC uses specific CAT Envelopes defined in SGP.22, then the UIMe SHALL fulfil the requirements related to the LUI.
    
- **15) ES21 `{ Device Application ⇒ LPR }`**
    
    The ES21 interface is used for exchanges between the LPR and a Device Application to trigger from the Device Application, a Profile content management session between a (D)PCMP and a Profile, or to send Notifications to the Device Application.
    
- **16) ES22 `{ Device Application ⇒ LPA }`**
    
    The ES22 interface is an LPA API used for exchanges between the LPA and a Device Application.
    
- **17) ESaa `{ LPR ⇒ eUICC }`**
    
    The ESaa interface is used between the LPR in the Device and the Profile of the eUICC for Profile content management through the use of the LPA as a proxy.
    
- **18) ESosup `{ eUICC ⇒ eUICC OS Manager }`**
    
    The eUICC OS Manager communicates with the eUICC through the ESosup interface. The ESosup interface delivers to the eUICC the commands to perform the eUICC OS Update.
    The implementation of the eUICC OS Manager and the ESosup are out of the scope of this specification.
    
- **19) ESoem `{ OEM ⇒ eUICC OS Manager }`**
    
    ESoem is the interface betweem OEM and the eUICC OS Manager. This interface can be used to receive the eUICC OS Update package(s) from the OEM and to dispatch it to the
    eUICC OS Manager in charge of the eUICC OS Update. The implementation of this interface is out of the scope of this specification but it has to deliver, together with the eUICC OS Update package(s), a minimum set of information.
    
- **20) ESapp `{ Device Application ⇒ Operator }`**
    
    The ESapp interface is used for exchanges between a Device Application and the Operator.
    The exchanges are triggered by the Device Application.
    GSMA PRD Specification TS.43 [54] is an example for the protocol to use on the ESappinterface.
    
- **21) Esci `{ CI ⇒ SM-DP+/SM-DS/EUM }`**
    
    ESci is the interface between the CI and the SM-DP+ / the SM-DS / the EUM, used by the SM-DP+, SM-DS and EUM to request a certificate and to retrieve the certificate revocation
    status.
