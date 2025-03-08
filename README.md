## Remote SIM Provisioning
>
>Remote SIM provisioning is a specification realized by GSMA that allows consumers to remotely activate the subscriber identity module (SIM) embedded in a portable device such as a smart phone, smart watch, fitness band or tablet computer. The specification was originally part of the GSMA's work on eSIM and it is important to note that remote SIM provisioning is just one of the aspects that this eSIM specification includes.

#### GSMA
>
>The GSM Association (commonly referred to as 'the GSMA' or Global System for Mobile Communications, originally Groupe Spécial Mobile) is a non-profit industry organisation that represents the interests of mobile network operators worldwide. More than 750 mobile operators are full GSMA members and a further 400 companies in the broader mobile ecosystem are associate members.

---
## Persona and Interactions for RSP
- **Consumer** : Sends intent by selecting a telco/data plan from an array or list of plans provided by _**MNO**(Mobile Network Operator)_.
- **MNO** : Orders _**SM-DP+**(Subscription Manager Data Preparation)_ to create an eSIM profile of the selected telco/data plan and delivers it to respective user device.
- **SM-DP+** : A server-side platform that manages eSIM profiles, prepares eSIM profiles with carrier information and credentials, enables communication between the device and the carrier network via _**LPA**(Local Profile Assistant)_ and securely stores and delivers eSIM profiles to devices.
- **LPA** : A system application, a software component within eSIM-enabled devices that manages eSIM profiles, interacts with the _**eUICC**(embedded Universal Integrated Circuit Card) chip_ within the device to store and manage eSIM profile, enabling seamless downloading, installation, and management of mobile network profiles without needing physical SIM cards.
- **eUICC Chip** : Simply put, it's a SIM card component that lets you switch mobile network operators (MNOs) remotely.
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

The Remote SIM Provisioning Architecture, with multiple entities interacting with reach other via secure routes and rules called Interfaces 
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

## Problem
_The problem with current RSP lies in trust, security, transparency, and automation in the process of remote SIM provisioning (RSP), which could potentially be solved using smart contracts and modern cryptography._

### The challenges:
1. **Trust Between Service Providers and Consumers**: Consumers must trust the remote provisioning process carried out by mobile operators or third-party service providers to be secure and private. Currently, this process requires reliance on intermediaries (like Subscription Managers) to manage SIM profiles and switch between mobile operators. This raises concerns about data security, privacy, and the handling of SIM profiles.

2. **Complexity in Profile Management**: Managing multiple profiles, especially when different service providers are involved, can be cumbersome. The current system involves centralized entities, making it prone to inefficiencies or even misuse of consumer data.

3. **Manual Processes and Delays**: Even though remote provisioning allows flexibility, manual intervention is still required at various stages (like authentication, profile switching, and payment settlement). This introduces potential delays and human errors.

4. **Unnecessary TLS Encapulation**: The security of RSP depends unnecessarily on it being encapsulated in a TLS tunnel, Interfaces within RSP over TLS are prone to passive adversaries.

5. **Privacy within the Protocol**: The RSP protocol lacks robust privacy measures to safeguard interactions between entities. Sensitive information, such as unique identifiers, is frequently shared during provisioning and profile switching. This exposure increases the risk of data leaks and unauthorized tracking, as adversaries can correlate interactions to identify users and their network preferences.

6. **No User Plane Data Integrity**: The current RSP protocol fails to ensure the integrity of user plane data, leaving it vulnerable to tampering or unauthorized modification. This issue is critical as compromised user plane data can lead to security risks, such as data corruption, injection attacks, or unauthorized access to network resources.

---

### The main issue with current [RSP](https://en.wikipedia.org/wiki/Remote_SIM_provisioning)
>
>The current RSP standard that remotely provision eSIM to user devie is based on a mechanism which revolves around exchanging keys and signing certificates between the device and the mobile network operator (MNO). These keys and certificates are used to verify the authenticity of the device and establish a secure and encrypted connection.
>And the security relies on trusted parties (central authority), The device manufacturers here play a crucial role along with OS to make sure not reveal eSIM profile.
>This also makes the environment restricted and later a closed industry.
>>

### Resolved Issue
>
>Independent service providers to transmit commands of loading profiles to SIM-cards in the device has been amended and the possibility to store arrays of profiles in Independent certified data centres (Subscriptions manager) has appeared.

#### eSIM Smart COntract Suite
With the [open source eSIM Smart Wallet](https://github.com/Blockchain-Powered-eSIM/smart-contract-suite) we have resolved the issue that gets introduced in the eSIM stack based on current RSP by removiing the possibility to store arrays of profiles in Independent certified data centres (Subscriptions manager), 
Actually , 
- eSIM Smart Wallet allows users to own their profiles and remove the requirements to store profiles in data centres,
- Provides well synchronization, security, and interoperability in subscription management which certified data centers are having issues with and it's tricky to keep everything secure, synced, and working smoothly.

---

# Open Source Remote SIM Provisioning (OpenRSP)
>
>OpenRSP, an Open Source [Remote SIM Provisioning](https://github.com/Blockchain-Powered-eSIM/eSIM-Wallet/wiki/Remote-SIM-Provisioning) protocol, for modern digital world, where everyone around the globe are connected(more connecting everyday) with telecom and data networks.
>The core of all the network protocols is cryptography, provides solutions to big domain of problems from privacy to security, integrity to authenticity and thus is the core of the modern digital world we all live in.
>The infrastructure supporting global connectivity relies on highly secure, proven cryptographic protocols that protect data and communication across diverse networks. Using mobile device , everyone is connected and rely on telecom network in all circumstances.
>To maintain user/consumer/everyone's data privacy, integrity, authencticity and security openRSP leverage modern cryptography and communication prootocols and with Smart Contracts it introduces ownership which hasn't been really looked into the telco industry on the cosumer side.
>With modern tech, secure-by-design and open source principle , OpenRSP delivers a trustless system in telecom industry which allows consumers to do more than just communicate.

# Abstract

OpenRSP, an Open Source Remote SIM Provisioning protocol, represents a new era in mobile connectivity, addressing the limitations of traditional systems while ensuring robust security, privacy, and user ownership. As the world becomes increasingly connected through telecom and data networks, the reliance on secure communication protocols is paramount. Cryptography plays a vital role in solving fundamental issues related to privacy, security, integrity, and authenticity, which form the foundation of modern digital infrastructure. As a protocol, RSP is continuosly evolvolving and it'll be the same until consumers have full ownership. Current RSP standards are dependent on central authority for trust, where device manufacturers and mobile network operators (MNOs) control the provisioning of eSIM profiles and by-design the ownership of consumer eSIM profile is held by Operators. Security is derived by exchange of keys and certificates between devices and MNOs, leading to a restricted and closed environment that lacks transparency and user empowerment. Authentications within the server reveals sensitive information and complexity can be improved by improving the design.
OpenRSP leverages modern cryptographic protocols and integrates smart contract technology to introduce a trustless system, removing reliance on traditional trusted parties. By decentralizing the control over eSIM profiles and allowing consumers to own and manage their profiles independently, OpenRSP empowers users in ways previously unexplored in the telecom industry. This innovative approach not only enhances security but also promotes greater transparency and consumer rights.
Through the use of the open source eSIM Smart Wallet, OpenRSP resolves key issues inherent in the current RSP stack. It removes the need for profiles to be stored in centralized data centers and enables independent service providers to load profiles directly onto devices. This shift enhances user control, ensuring that consumers have full ownership of their digital identity and profiles.
Built on the principles of secure-by-design, OpenRSP establishes a decentralized, transparent, and user-centric approach to mobile provisioning. It redefines how we view connectivity, empowering users to do more than just communicate while fostering a more open and secure telecom ecosystem.

## Modern Cryptography
Modern Cryptoraphy helps in securing digital information, interactions between parties, tranactions and distributed computations. Also provides many tools to avail data integrity, introduce or improve privacy withing a protocol. There are many cryptographic primitives that can be used to design and improve RSP as a protocol, ZKP(Zero Knowledge Proofs), FHE(Fully Homomorphic Encryption), WE(Witness Encryption), FE(Functional Encryption). For now, we'll focus on a ZKP and move to examine other primitives later...

### Zero Knowledge Proving System (ZKPs)
Zero Knowledge Proofs and Proving Systems is a groundbreaking tool to achieve goals for modern digital world.
In the world of sharing, exposure or leakage of information, ZKP provides a protocol where prover share nothing but the proof that he holds the right information to follow the respective protocol and verifier verifies accordignly.

- **Can you prove you followed the process without revealing the underlying details?**
- **Can you prove an outcome is valid without disclosing the steps that led to it?**
- **Can you verify a claim without revealing anything beyond the claim itself?**

of-course you need to define what it means not to reveal anything else.

**These question leads to the birth of first Zero Knowledge Proof(by a different name).**

### Zero Knowledge Proofs in RSP,

1. ZKCX : Certificate Authentication without Revealing the Certificate Contents and ZKProofs for Revocation Checking
2. XX (ZKP for EID Privacy) (_if this is only the motive and system entity's aren't dependent, then just hiding EID using another primitive will be better choice_) **OT**
3. XX (ZK SM-DP+ Authentication) (_the sm-dp+ server have all the sensitive information at the end of mutual auth, the data being stored keeps adding on throughout auth, even if you hide half of the data stored, you still have everything much to identify end user) **Tackle with 2PC LPA <-> SM-DP+ and SM-DP+ <-> eUICC**
4. ZK Secure TLS Communication

## Directions for advancements in privacy of RSP as a protocol

### Trust Distribution, same certficates

![Proving X.509 certificates with ZKP](assets/images/OpenRSP_CI_ZKP_Solution.png)

While the GSMA holds the authority to issue the X.509 certificates, and the intermediate CAs issue it to the intermediates/end-entity below them in hierarchy, the end-entities need to Trust the Proof chain and they are pretty much clueless about the authenticity of the X.509 certificates held by their "higher-ups" in the chain until each certificate has been verified every time. These certificates act as the proof of authority of the CA and, the X.509 certificate itself is shared between the various entites participating in the RSP and these certificates contain various private/sensitive data.  
The solution aims to remove the trust from the GSMA CI to the ZKP Verifier (which verifies the authenticity of the X.509 certificate and the verifier is publicly available on-chain ready to be verified by anyone) and each entity creates their own ZKP proof for their certificate. This allows the protocol to authenticate the participants without revealing their X.509 certificates, or any sensitive data in the certificates.  
A central registry will record the proofs on-chain and these proofs might be used to prove the authenticity of an existing certificate (until a certain time perios) without having the need to generate a new proof for every interaction happening between the same set of entities in a given span of time.  
> The idea is still under development and there might be significant changes in future.

### More Privacy, no certificates

It includes modern authentication for eSIMs, ensuring their validity and enabling users to prove ownership of eSIM profiles to network providers without compromising their private credentials. One key aspect of our approach is the utilization of the eUICC unique identifier ([EID](./eUICC/EID/README.md)) to create a Secure Identifier (SSID/ZKID/DID). The EID is inherently unique and tied to the device's hardware, serving as a robust form of two-factor security. By combining this hardware-backed identifier with “*something you know*" (e.g., user credentials) and "*something you are*" (e.g., biometric data), we can enhance privacy-focused encryption and authentication for outsourced data and industry-wide collaboration. Thinking about OpenRSP incorporating the secure identifier, an advanced framework that leverages state-of-the-art cryptographic techniques to address these challenges.

OpenRSP can incorporate two key innovations, Identity-Based Non-Interactive Key Exchange (IBNIKE) for Secure Identifier (SSID/ZKID) generation and Multi-Party Oblivious Transfers (MPOT) using Garbled Circuits for secure interactions within the RSP ecosystem. IBNIKE enables the generation of unique, privacy-preserving identifiers for end users without compromising their personal data. MPOT ensures secure collaboration between multiple entities involved in eSIM provisioning, safeguarding user privacy and system integrity.

OpenRSP represents a significant advancement in eSIM provisioning technology, offering a secure and privacy-preserving solution that meets the evolving needs of mobile network operators, device manufacturers, and end users. This draft will continue to improve and serve as a comprehensive guide for stakeholders interested in adopting OpenRSP to enhance the security and privacy of their eSIM ecosystems.

---
We will be providing a detailed analysis of the theory, implementation, challenges and potential benefits of incorporating these advanced cryptographic techniques into eSIM technology.
Our result will demonstrate that the proposed framework not only significantly improves the security and privacy of the RSP process but also lays the foundation for a more trustworthy and collaborative environment in the digital communication domain.

Work in progress . . .
