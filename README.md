# OpenRSP(Open Source Remote SIM Provisioning)
>
> ##### _Democratizing Consumer Telco Connectivity_
> _Abstract_ , Emerging eSIM technology is transforming telecommunications by enabling users to obtain mobile subscriptions over- the-air (OTA) through remote SIM profile provisioning.
> Unlike traditional SIM cards, eSIMs are embedded directly into devices via an Embedded Universal Integrated Circuit Card (eUICC), eliminating the need for physical stores and reducing the risk of SIM swap attacks.
> This shift democratizes consumer telecom infrastructure, enhances user experience, and lays the groundwork for a more secure, flexible mobile ecosystem.
>
>_At the heart of this ecosystem_ lies **Remote SIM Provisioning (RSP)**, the software protocol that manages eSIM life-cycle and securely delivers eSIM profiles to secure hardware(user device., embedded UICC chip) through multiple interacting components.
> When a user selects a subscription plan, the Local Profile Assistant (LPA) on the device sends an intent to the Subscription Manager Data Preparation (SM-DP+) server, which generates and certifies the profile using Public Key Infrastructure (PKI) and X.509 certificates issued by GSMA-compliant entities.
> The profile is then authenticated and installed on the eUICC, allowing seamless access to cellular services.
>
>_Despite its promise_, RSP remains immature, with inconsistent security implementations leading to vulnerabilities.
> **_The telecom industry continues to face data breaches, and as eSIM adoption accelerates — with half a billion devices shipped in 2023 and projections of 9 billion by 2030 — ensuring interoperability and robust security across devices and carriers becomes increasingly urgent._**
>
> _We present OpenRSP_, a decentralized protocol addressing the current RSP vulnerablities and enhances security, privacy, and interoperability of multiple parties responsible to securely provision eSIMs through _cutting-edge cryptographic techniques, smart contracts, decentralized blockchains and Trusted Execution Environment(TEEs)_.
> OpenRSP replaces centralized trust points with blockchain and smart contracts, enabling independent verification of transactions. It integrates zero-knowledge proofs (ZKPs) within the X.509 certificate chain to protect sensitive information and introduces Trusted Execution Environments (TEEs) for user plane data integrity with local-first compute. By eliminating single points of failure and empowering entities to collaboratively manage profiles in a trustless environment, OpenRSP addresses the critical challenges of RSP. This approach fortifies telecom infrastructure, safeguards consumer data, and promotes a more resilient, open, and secure mobile ecosystem.

# Preliminaries

## eSIM
>
> **eSIM exemplifies hardware-software co-design by integrating secure hardware with flexible software to enable seamless, remote mobile connectivity.**

## Remote SIM Provisioning
>
>Remote SIM provisioning is a specification realized by GSMA that allows consumers to remotely activate the subscriber identity module (SIM) embedded in a portable device such as a smart phone, smart watch, fitness band or tablet computer. The specification was originally part of the GSMA's work on eSIM and it is important to note that remote SIM provisioning is just one of the aspects that this eSIM specification includes.

#### GSMA
>
>The GSM Association (commonly referred to as 'the GSMA' or Global System for Mobile Communications, originally Groupe Spécial Mobile) is a non-profit industry organisation that represents the interests of mobile network operators worldwide. More than 750 mobile operators are full GSMA members and a further 400 companies in the broader mobile ecosystem are associate members.

---
## Persona and Interactions for RSP
1. **Consumer** : Sends intent by selecting a telco/data plan from an array or list of plans provided by _**MNO**(Mobile Network Operator)_.
2. **MNO** : Orders _**SM-DP+**(Subscription Manager Data Preparation)_ to create an eSIM profile of the selected telco/data plan and delivers it to respective user device.
3. **SM-DP+** : A server-side platform that manages eSIM profiles, prepares eSIM profiles with carrier information and credentials, enables communication between the device and the carrier network via _**LPA**(Local Profile Assistant)_ and securely stores and delivers eSIM profiles to devices.
4. **LPA** : A system application, a software component within eSIM-enabled devices that manages eSIM profiles, interacts with the _**eUICC**(embedded Universal Integrated Circuit Card) chip_ within the device to store and manage eSIM profile, enabling seamless downloading, installation, and management of mobile network profiles without needing physical SIM cards.
5. **eUICC Chip** : Simply put, it's a SIM card component that lets you switch mobile network operators (MNOs) remotely.
<img width="937" alt="Screenshot 2024-10-14 at 9 10 32 PM" src="https://github.com/user-attachments/assets/b8b69571-2d4e-4e80-850a-b5e867434349">

# eSIM 
The eSIM _technology_ combines the eUICC chip(hardware) and SM-DP+(software),  
defines the rules as a _protocol_ for communication between multiple entities, user, MNO, SM-DP+, LPA & eUICC and  
finally as a _system_, integrates these elements to **achieve secure remote SIM provisioning**. 
>
>📰 **Half a billion** eSIM-capable devices were shipped in 2023, **Over 9 billion** to be shipped by 2030, **Nearly 70%** proportion cellular devices eSIM capable by 2030.
>

## Structure
eSIMs adopt a domain-based architecture to separate functionalities and enhance security. This approach divides the SIM's roles into distinct domains, each serving specific purposes.

**The concept of "domains" is a structural approach to segregate the functionalities and responsibilities within the SIM.**

In eUICC  and eSIM (embedded Subscriber Identity Module) technology, domains are used as abstractions to segregate different functionalities, stakeholders, and operational scopes. This abstraction ensures clear separation of concerns and provides flexibility, scalability, and security in managing mobile connectivity. Here are the main domains commonly used:

> Unlike traditional SIM cards, eSIMs can be integrated into a System-on-Chip (SoC) or used as upgradable components via APIs like the Android 9 eSIM APIs. GSMA certification mandates that sensitive personalization data—such as Ki, OPc, and 5G keys—be securely processed within the eSIM hardware, eliminating the risk of data extraction. A critical feature of eSIMs is enterprise ownership, granting full control over security configurations, applications, and the selection of operator profiles.  

## Domains in eSIM
#### 1. Subscription Management Domain
The **subscription management domain** handles the provisioning, management and deletion of Operator Profiles on eUICC-enabled devices. There are two components in this domain:
- **a)** SM-DP (Subscription Manager - Data Preparation)
    - Typically managed by the MNOs (Mobile Network Providers).
    - Generates and encrypts eSIM profiles.
    - Preapares profiles for provisioning and send encrypted profiles to the SM-SR for delivery to target eUICC.

- **b)** SM-SR (Subscription Manager - Secure Routing)
    - Managed by a trusted thrid-party or MNO.
    - Acts as a conrtrol plane for SM-DP and eUICC interactions.
    - Responsible for securely routing the encrypted profile from SM-DP to eUICC.

#### 2. eUICC Domain
The **eUICC domain** provides a secure, tamper-resistant hardware platform for hosting multiple operator profiles. This domain consists of following sub-domains:
- **a)** Profile Domain
    - Respresents individual operator profiles stored on eUICC.
    - Contains credentials and settings necessary for network authentication.
    - Multiple profiles can exist on an eUICC but the number of active profiles depends on device capabailities.
- **b)** Platform Domain
    - Manages overall eUICC system functionalities.
    - Provides scurity features and enforces policies for profile management.
    - Facilitates communication between the eUICC, device, and subscription management systems.

#### 3. Device Domain
The **device domain** domain is responsible for interactions between eUICC and the device hosting it. This domain consists of following sub-domains:
- **a)** Host Device Domain
    - Represents the hardware device (e.g., smartphone, tablet, IoT device) containing the eUICC.
    - Communicates with the eUICC for operations such as profile activation, deactivation, or switching.
    - Runs the mobile OS or applications interacting with the eUICC.
- **b)** User Interface Domain
    - Provides a user-friendly interface for managing eSIM profiles (e.g., selecting a profile to activate or deleting a profile).
    - Accessible via the settings or a dedicated application.
    - Encapsulates functionalities of LPA (Local Profile Assistant)

#### 4. Connectivity Domains
The **connectivity domain** encompasses the interfaces and protocols used for connectivity and communication. It consists of fololowing sub-domains:
- **a)** Over-The-Air (OTA) Domain
    - Includes mobile network infrastructure used for profile activation and connectivity.
    - Uses secure protocols (e.g., GSMA’s RSP standard) to communicate between the SM-SR and eUICC.
    - Enables the secure provisioning of new keys, certificates, or updates to the eSIM.
- **b)** Communication Network Domain
    - Includes mobile network infrastructure used for profile activation and connectivity.
    - Ensures the eSIM profile works with the corresponding MNO.

#### 5. Security Domain
The **security domain** is dedicated to manage sensitive cryptographic operations. It is fundamental in eUICC and eSIM protocol to protect data and ensure trustworthiness. It has the following sub-domains:
- **a)** Secure Element (SE) Domain
    - The hardware-based tamper-resistant element hosting the eUICC.
    - Protects credentials, cryptographic keys, and profiles from unauthorized access.
- **b)** Cryptographic Domain
    - Enforces security protocols and encryption for profile delivery, installation, and communication.
    - Uses Public Key Infrastructure (PKI) and other cryptographic methods for authentication and data integrity.

This domain-based architecture adds a layer of abstraction and security, allowing eSIMs to serve it purpose ensuring compliance with security and regulatory requirements.

### eSIM Installation
<img width="911" alt="Screenshot 2024-10-09 at 4 33 40 PM" src="https://github.com/user-attachments/assets/837164db-3ade-431b-a16f-53724a9b87b0">
---

### X.509 Certificates and Chain of Trust
The Chain of Trust in X.509 certificates is a hierarchical structure used to verify the authenticity of digital certificates.  
It begins with a Root Certificate Authority (Root CA), which is inherently trusted and widely distributed in systems and browsers.  
The Root CA issues and signs certificates for Intermediate Certificate Authorities (Intermediate CAs), which in turn issue certificates to End-Entities (Leaf Certificates), such as websites or users.  
To establish trust, each certificate in the chain must be verified by the certificate above it, with the process starting from the end-entity’s certificate and moving up to the intermediate and root certificates. If any part of this chain is invalid, revoked, or tampered with, the entire chain is considered untrusted, which compromises the security of the system. Read more about Chain of Trust [here](./CI/Readme.md)

---

# RSP Architecture:
> [!NOTE]
> All the acquired knowledge and new RnD is started from [RSP Architecture SGP.21 V3.1](https://www.gsma.com/solutions-and-impact/technologies/esim/wp-content/uploads/2023/12/SGP.21-V3.1.pdf) with focus on consumer RSP.
> 
> Refer to this [document](https://guyphy.notion.site/Supplementary-Reading-1299492854b480c78b66f080a823bb4b) for detailed Consumer eSIM Profile Info.

The Remote SIM Provisioning Architecture, The interaction between components and inner working is represented by ES modules.
![RSP-Architecture](https://github.com/user-attachments/assets/30bb39db-5c26-4c9c-b46e-1a01452525bf)

### Major Componenets:

- Certificate Issuer(CI)
- Operator
- Mobile Service Provider
- SM-DP+ (Data Preparation)
- SM-DS (Discovery Service)
- LPA (Device App)
- eUICC (embedded chip)

### Principles

All parties either implementing or operating systems based on these specifications should be aware that any data items passed between system elements that can be used to identify an individual can be classified as personal data (as defined in the General Data Protection Regulation (EU) 2016/679). Responsibility for the management of Personal Data and compliance with any necessary legislation lies with implementing and operating organisations, according to each organisation’s respective legal status with respect to the data processes (i.e. whether the entity acts as a data controller or as a data processor).

### High Level Authorized Parties
>The requirement of GSMA certification is that personalisation packet is decoded inside the chip and so there is **no way to dump Ki, OPc and 5G keys.**
>Another important aspect is that the **eSIM is owned by the enterprise**, and this means that the enterprise now has full control of the security and applications in the eSIM, and which operators profiles are to be used.

- root GSMA CI
- sub CI
- EUM
- OEM
- Operator

---
# Governance Of Secure Elements
‼️ Using embedded Secure Elements inside the smartphone is a matter of business agreements and governance, not a technological issue.  

### 1. Embedded Secure Element
- Owned by smartphone manufacturer
- eSE management controlled by smartphone manufacturer
- Secure provisioning addressed using Secure Element Issuer Trusted Service manager (SEI-TSM) server

### 2. Embedded SIM
- Owned by smartphone manufacturer
- Root Certificate of GSMA pre-installed and profile download contralled by the GSMA
- Secure Provisioning done with Subscription Manager Data Preparation(SM-DP) server

### 3. Embedded SIM with SAM(Secured Application for Mobile)
- Owned by smartphone manufacturer
- Root Certificate Of Member State pre-installed
- Secure provisioning done with Secured Application for Mobile Service Manager (SAM-SM)

💡**Industries who found the way to access secure elements so far** are:
- Mobile Network Operator
- Banks and Payment Providers
- Transports
- Car Makers

> [!NOTE]
> As we have now touched every aspect of eSIM and RSP, we move forward with the problems~

---

## Problem
_The problem with RSP lies in trust, security, transparency, and automation in the process of remote SIM provisioning (RSP), which could potentially be solved using smart contracts and modern cryptography._
>
>The [RSP](https://en.wikipedia.org/wiki/Remote_SIM_provisioning) standard that remotely provision eSIM to user devie is based on a mechanism which revolves around exchanging keys and signing certificates between the device and the mobile network operator (MNO). These keys and certificates are used to verify the authenticity of the device and establish a secure and encrypted connection.
>And the security relies on trusted parties (central authority), The device manufacturers here play a crucial role along with OS to make sure not reveal eSIM profile.
>This also makes the environment restricted and later a closed industry.

### ❗ [eSIM Problem Summary](https://github.com/Blockchain-Powered-eSIM/Kokio-docs/wiki/Problems-With-eSIMs)

## Challenges:
1. **Trust Between Service Providers and Consumers**: Consumers must trust the remote provisioning process carried out by mobile operators or third-party service providers to be secure and private. Currently, this process requires reliance on intermediaries (like Subscription Managers) to manage SIM profiles and switch between mobile operators. This raises concerns about data security, privacy, and the handling of SIM profiles.

2. **Complexity in Profile Management**: Managing multiple profiles, especially when different service providers are involved, can be cumbersome. The current system involves centralized entities, making it prone to inefficiencies or even misuse of consumer data.

3. **Manual Processes and Delays**: Even though remote provisioning allows flexibility, manual intervention is still required at various stages (like authentication, profile switching, and payment settlement). This introduces potential delays and human errors.

4. **Unnecessary TLS Encapulation**: The security of RSP depends unnecessarily on it being encapsulated in a TLS tunnel, Interfaces within RSP over TLS are prone to passive adversaries. TLS isn’t just a privacy layer — it's doing core security work, which is brittle.

5. **Privacy within the Protocol**: The RSP protocol lacks robust privacy measures to safeguard interactions between entities. Sensitive information, such as unique identifiers, is frequently shared during provisioning and profile switching. This exposure increases the risk of data leaks and unauthorized tracking, as adversaries can correlate interactions to identify users and their network preferences.

6. **No User Plane Data Integrity**: The current RSP protocol fails to ensure the integrity of user plane data, leaving it vulnerable to tampering or unauthorized modification. This issue is critical as compromised user plane data can lead to security risks, such as data corruption, injection attacks, or unauthorized access to network resources.

### ❗ [RSP Failure Summary](https://github.com/orgs/Blockchain-Powered-eSIM/discussions/1#discussioncomment-12732458)

---

# Open Source Remote SIM Provisioning (OpenRSP)
>
>An **Open Source Democratized [Remote SIM Provisioning](https://github.com/Blockchain-Powered-eSIM/eSIM-Wallet/wiki/Remote-SIM-Provisioning)**, providing open ways for entities collaborate for respective operations and derive benefits accordingly.
>_**Protecting sensitive information**_ of entities and users with strong access controls and educating to upgrade respectively,
>_**Introducing User plane data integrity with gurantee, Ownership with verifiability and improving privacy within the protocol**_ by leveraging
>_**state-of-art cryptography & TEEs, blockchain & smart contracts**_ to addresse the problem and challenges faced in RSP , manage end-to-end eSIM operations and maintain data privacy & security , integrity & authencticity.
>_A system for a modern digital world, where everyone around the globe are connected(more connecting everyday) with telecom and data networks._
>With modern tech, secure-by-design and open source principle , **OpenRSP delivers a trustless system in telecom industry which allows consumers to do more than just communicate.**

# Introduction

THe rapid adoption of eSIM technology is revolutionizing elecommunications by enabling users to remotely provi- sion and manage mobile subscriptions without physical SIM cards. At the center of this transformation lies Remote SIM Provisioning (RSP), a protocol designed to securely deliver and manage eSIM profiles over-the-air (OTA). This advance- ment streamlines consumer access to mobile networks, reduces logistical overhead, and mitigates risks like SIM swap attacks. Yet, the current RSP ecosystem remains reliant on centralized trust authorities — device manufacturers and mobile network operators (MNOs) — limiting transparency, user ownership, and security resilience.
In the existing model, profile provisioning and lifecycle management depend on secure exchanges of keys and certifi- cates, with authentication processes that expose sensitive data to centralized servers. This centralized architecture introduces single points of failure, while the lack of user-controlled cryp- tographic processes leaves consumers without true ownership of their eSIM profiles. As the ecosystem grows — with an estimated 9 billion eSIM-enabled devices expected by 2030 — these limitations pose significant scalability and security challenges.

In the existing model, profile provisioning and lifecycle management depend on secure exchanges of keys and certifi- cates, with authentication processes that expose sensitive data to centralized servers. This centralized architecture introduces single points of failure, while the lack of user-controlled cryp- tographic processes leaves consumers without true ownership of their eSIM profiles. As the ecosystem grows — with an estimated 9 billion eSIM-enabled devices expected by 2030 — these limitations pose significant scalability and security challenges.

Open Source Remote SIM Provisioning (OpenRSP) ad- dresses these challenges by decentralizing control, removing reliance on traditional trusted parties, and empowering users with cryptographic ownership of their profiles. By leverag- ing blockchain, smart contracts, and zero-knowledge proofs, OpenRSP eliminates the need for centralized certificate author- ities, allowing entities and consumers to verify transactions independently. The protocol also aims to utilise TEEs to execute for more consumer side operations on user equipment and define user-plane data integrity with scope of gurantee and strengthening overall security.
Through an open-source, secure-by-design approach, OpenRSP redefines mobile provisioning, transforming eSIM infrastructure into a transparent, resilient, and user-centric ecosystem. This evolution not only enhances security and privacy but also democratizes access to mobile connectivity, paving the way for a future where users have complete autonomy over their digital identities.

OpenRSP, an Open Source Remote SIM Provisioning protocol, represents a new era in mobile connectivity, addressing the limitations of traditional systems while ensuring robust security, privacy, and user ownership. As the world becomes increasingly connected through telecom and data networks, the reliance on secure communication protocols is paramount. Cryptography plays a vital role in solving fundamental issues related to privacy, security, integrity, and authenticity, which form the foundation of modern digital infrastructure. As a protocol, RSP is continuosly evolvolving and it'll be the same until consumers have full ownership. Current RSP standards are dependent on central authority for trust, where device manufacturers and mobile network operators (MNOs) control the provisioning of eSIM profiles and by-design the ownership of consumer eSIM profile is held by Operators. Security is derived by exchange of keys and certificates between devices and MNOs, leading to a restricted and closed environment that lacks transparency and user empowerment. Authentications within the server reveals sensitive information and complexity can be improved by improving the design.
OpenRSP leverages modern cryptographic protocols and integrates smart contract technology to introduce a trustless system, removing reliance on traditional trusted parties. By decentralizing the control over eSIM profiles and allowing consumers to own and manage their profiles independently, OpenRSP empowers users in ways previously unexplored in the telecom industry. This innovative approach not only enhances security but also promotes greater transparency and consumer rights.
Through the use of the open source eSIM Smart Wallet, OpenRSP resolves key issues inherent in the RSP stack. It removes the need for profiles to be stored in centralized data centers and enables independent service providers to load profiles directly onto devices. This shift enhances user control, ensuring that consumers have full ownership of their digital identity and profiles.
Built on the principles of secure-by-design, OpenRSP establishes a decentralized, transparent, and user-centric approach to mobile provisioning. It redefines how we view connectivity, empowering users to do more than just communicate while fostering a more open and secure telecom ecosystem.

## Approach

Our approach is open source and aims to democratize remote SIM provisioning (RSP) by maintaining sensitive information confidential, enhancing privacy, and strengthen- ing security within the protocol. We address the existing issues and technical challenges in RSP by leveraging smart contracts, blockchain, and modern cryptographic primitives.
Smart contracts eliminate the need for centralized, certified data centers to manage eSIM profiles, decentralizing con- trol and giving consumers true ownership of their digital identities. By integrating zero-knowledge proofs (ZKPs) for proving rather disclosure of information and TEEs for secure local computation, OpenRSP ensures a trustless, verifiable, and privacy-preserving ecosystem. Blockchain anchors the protocol’s security, while distributed consensus replaces the reliance on mobile network operators (MNOs) and device manufacturers as sole trust authorities. This comprehensive approach not only mitigates security vulnerabilities but also fosters an open, collaborative environment where stakeholders, entities, and users collectively contribute to the evolution of a more transparent and resilient telecom infrastructure.

## Modern Cryptography
Modern Cryptoraphy helps in securing digital information, interactions between parties, transactions and distributed computations. Also provides many tools to avail data integrity, introduce or improve privacy withing a protocol. There are many cryptographic primitives that can be used to design and improve RSP as a protocol, ZKP(Zero Knowledge Proofs), FHE(Fully Homomorphic Encryption), WE(Witness Encryption), FE(Functional Encryption). For now, we'll focus on a ZKP and move to examine other primitives later...

### Zero Knowledge Proving System (ZKPs)
Zero Knowledge Proofs and Proving Systems is a groundbreaking tool to achieve goals for modern digital world.
In the world of sharing, exposure or leakage of information, ZKP provides a protocol where prover share nothing but the proof that he holds the right information to follow the respective protocol and verifier verifies accordignly.

- **Can you prove you followed the process without revealing the underlying details?**
- **Can you prove an outcome is valid without disclosing the steps that led to it?**
- **Can you verify a claim without revealing anything beyond the claim itself?**

of-course you need to define what it means not to reveal anything else.

**These question leads to the birth of first Zero Knowledge Proof(by a different name).**

### Zero Knowledge Proofs in RSP,

1. **zkCX** _(Zero Knowledge Certificate Exchange)_ : Certificate Authentication without Revealing the Certificate Contents and ZKProofs for Revocation Checking
2. **XX (ZKP for EID Privacy)** (_if this is only the motive and system entity's aren't dependent, then just hiding EID using another primitive will be better choice_) **OT**
3. **XX (ZK SM-DP+ Authentication)** (_the sm-dp+ server have all the sensitive information at the end of mutual auth, the data being stored keeps adding on throughout auth, even if you hide half of the data stored, you still have everything much to identify end user) **Tackle with 2PC LPA <-> SM-DP+ and SM-DP+ <-> eUICC**
4. **ZK Secure TLS Communication** : TLS Tunnel Dependency, eSIM Profile activation-code approach is critically dependent on TLS to protect the activation code. TLS should remain only as a privacy layer (e.g., to hide identifiers from network observers).


## Directions for advancements in privacy of RSP as a protocol

### Trust Distribution, same certficates

![Proving X.509 certificates with ZKP](assets/images/OpenRSP_CI_ZKP_Solution.png)

While the GSMA holds the authority to issue the X.509 certificates, and the intermediate CAs issue it to the intermediates/end-entity below them in hierarchy, the end-entities need to Trust the Proof chain and they are pretty much clueless about the authenticity of the X.509 certificates held by their "higher-ups" in the chain until each certificate has been verified every time. These certificates act as the proof of authority of the CA and, the X.509 certificate itself is shared between the various entites participating in the RSP and these certificates contain various private/sensitive data.  
The solution aims to remove the trust from the GSMA CI to the ZKP Verifier (which verifies the authenticity of the X.509 certificate and the verifier is publicly available on-chain ready to be verified by anyone) and each entity creates their own ZKP proof for their certificate. This allows the protocol to authenticate the participants without revealing their X.509 certificates, or any sensitive data in the certificates.  
A central registry will record the proofs on-chain and these proofs might be used to prove the authenticity of an existing certificate (until a certain time perios) without having the need to generate a new proof for every interaction happening between the same set of entities in a given span of time.  
> The idea is still under development and there might be significant changes in future.

### More Privacy, No certificates

It includes modern authentication for eSIMs, ensuring their validity and enabling users to prove ownership of eSIM profiles to network providers without compromising their private credentials. One key aspect of our approach is the utilization of the eUICC unique identifier ([EID](./eUICC/EID/README.md)) to create a Secure Identifier (SSID/ZKID/DID). The EID is inherently unique and tied to the device's hardware, serving as a robust form of two-factor security. By combining this hardware-backed identifier with “*something you know*" (e.g., user credentials) and "*something you are*" (e.g., biometric data), we can enhance privacy-focused encryption and authentication for outsourced data and industry-wide collaboration. Thinking about OpenRSP incorporating the secure identifier, an advanced framework that leverages state-of-the-art cryptographic techniques to address these challenges.

OpenRSP can incorporate two key innovations, Identity-Based Non-Interactive Key Exchange (IBNIKE) for Secure Identifier (SSID/ZKID) generation and Multi-Party Oblivious Transfers (MPOT) using Garbled Circuits for secure interactions within the RSP ecosystem. IBNIKE enables the generation of unique, privacy-preserving identifiers for end users without compromising their personal data. MPOT ensures secure collaboration between multiple entities involved in eSIM provisioning, safeguarding user privacy and system integrity.

OpenRSP represents a significant advancement in eSIM provisioning technology, offering a secure and privacy-preserving solution that meets the evolving needs of mobile network operators, device manufacturers, and end users. This draft will continue to improve and serve as a comprehensive guide for stakeholders interested in adopting OpenRSP to enhance the security and privacy of their eSIM ecosystems.

---
We will be providing a detailed analysis of the theory, implementation, challenges and potential benefits of incorporating these advanced cryptographic techniques into eSIM technology.
Our result will demonstrate that the proposed framework not only significantly improves the security and privacy of the RSP process but also lays the foundation for a more trustworthy and collaborative environment in the digital communication domain.

Work in progress . . .
