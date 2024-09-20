# Open Source Remote SIM Provisioning
## Remote SIM Provisioning
>
>Remote SIM provisioning is a specification realized by GSMA that allows consumers to remotely activate the subscriber identity module (SIM) embedded in a portable device such as a smart phone, smart watch, fitness band or tablet computer. The specification was originally part of the GSMA's work on eSIM[3] and it is important >to note that remote SIM provisioning is just one of the aspects that this eSIM specification includes.

**[BELIEF]** _The problem with current RSP lies in trust, transparency, and automation in the process of remote SIM provisioning (RSP), which could potentially be solved using smart contracts and modern cryptography._

### The challenges:
1. **Trust Between Service Providers and Consumers**: Consumers must trust the remote provisioning process carried out by mobile operators or third-party service providers to be secure and private. Currently, this process requires reliance on intermediaries (like Subscription Managers) to manage SIM profiles and switch between mobile operators. This raises concerns about data security, privacy, and the handling of SIM profiles.

2. **Complexity in Profile Management**: Managing multiple profiles, especially when different service providers are involved, can be cumbersome. The current system involves centralized entities, making it prone to inefficiencies or even misuse of consumer data.

3. **Manual Processes and Delays**: Even though remote provisioning allows flexibility, manual intervention is still required at various stages (like authentication, profile switching, and payment settlement). This introduces potential delays and human errors.

## OpenRSP
>
>OpenRSP, an Open Source [Remote SIM Provisioning](https://github.com/Blockchain-Powered-eSIM/eSIM-Wallet/wiki/Remote-SIM-Provisioning) protocol, for modern digital world, where everyone around the globe are connected(more connecting everyday) with telecom and data networks. The core of all the network protocols is cryptography, provides solutions to big domain of problems from privacy to security, integrity to authenticity and thus is the core of the modern digital world we all live in. The infrastructure supporting global connectivity relies on highly secure, proven cryptographic protocols that protect data and communication across diverse networks. Using mobile device , everyone is connected and rely on telecom network in all circumstances. To maintain user/consumer/everyone's data privacy, integrity, authencticity and security openRSP leverage modern cryptography and communication prootocols and with Smart Contracts it introduces ownership which hasn't been really looked into the telco industry on the cosumer side. With modern tech, secure-by-design and open source principle , OpenRSP delivers a trustless system in telecom industry which allows consumers to do more than just communicate.

### The issue with current [RSP](https://en.wikipedia.org/wiki/Remote_SIM_provisioning)
>
>The current RSP standard that remotely provision eSIM to user devie is based on a mechanism which revolves around exchanging keys and signing certificates between the device and the mobile network operator (MNO). These keys and certificates are used to verify the authenticity of the device and establish a secure and encrypted connection.
>And the security relies on trusted parties, The device manufacturers here play a crucial role along with OS to make sure not reveal eSIM profile.
>This also makes the environment restricted and later a closed industry.
>>

### Resolved Issue
*With the [open source eSIM Smart Wallet](https://github.com/Blockchain-Powered-eSIM/smart-contract-suite) we have resolved the issue that gets introduced in the eSIM stack based on current RSP which is*
>
>The right of independent service providers to transmit commands of loading profiles to SIM-cards in the device has been amended and the possibility to store arrays of profiles in independent certified data centres (Subscriptions manager) has appeared.
>

#### Where eSIM Smart Wallet allows users to own their profiles and remove the requirements to store profiles in data centres.
---
# Abstract
OpenRSP, an Open Source Remote SIM Provisioning protocol, represents a new era in mobile connectivity, addressing the limitations of traditional systems while ensuring robust security, privacy, and user ownership. As the world becomes increasingly connected through telecom and data networks, the reliance on secure communication protocols is paramount. Cryptography plays a vital role in solving fundamental issues related to privacy, security, integrity, and authenticity, which form the foundation of modern digital infrastructure. Current RSP standards are dependent on trusted third parties, where device manufacturers and mobile network operators (MNOs) control the provisioning of eSIM profiles, limiting consumer ownership and flexibility. Security in these systems hinges on the exchange of keys and certificates between devices and MNOs, leading to a restricted and closed environment that lacks transparency and user empowerment.
OpenRSP leverages modern cryptographic protocols and integrates smart contract technology to introduce a trustless system, removing reliance on traditional trusted parties. By decentralizing the control over eSIM profiles and allowing consumers to own and manage their profiles independently, OpenRSP empowers users in ways previously unexplored in the telecom industry. This innovative approach not only enhances security but also promotes greater transparency and consumer rights.
Through the use of the open source eSIM Smart Wallet, OpenRSP resolves key issues inherent in the current RSP stack. It removes the need for profiles to be stored in centralized data centers and enables independent service providers to load profiles directly onto devices. This shift enhances user control, ensuring that consumers have full ownership of their digital identity and profiles.
Built on the principles of secure-by-design, OpenRSP establishes a decentralized, transparent, and user-centric approach to mobile provisioning. It redefines how we view connectivity, empowering users to do more than just communicate while fostering a more open and secure telecom ecosystem.

# RSP Architecture:
!NOTICE: All the traditonal knowledge and new RnD is started from [RSP Architecture SGP.21 V3.1](https://www.gsma.com/solutions-and-impact/technologies/esim/wp-content/uploads/2023/12/SGP.21-V3.1.pdf). The interaction between components and inner working is represented by `ES`.

The current Remote SIM Provisioning Architecture,
![RSP-Architecture](https://github.com/user-attachments/assets/30bb39db-5c26-4c9c-b46e-1a01452525bf)

### Major Componenets:

- Certificate Issuer(CI)
- Operator
- Mobile Service Provider
- SM-DP+
- SM-DS
- Device App
- LPA

### Outbound Interactions

- eUICC
- LPA
- USER

### High Level Authorized Parties

- EUM
- CI
- OEM
- Operator

---
### One approach for openRSP

It includes modern authentication for eSIMs, ensuring their validity and enabling users to prove ownership of eSIM profiles to network providers without compromising their private credentials. One key aspect of our approach is the utilization of the eUICC unique identifier (EID) to create a Secure Identifier (SSID/ZKID/DID). The EID is inherently unique and tied to the device's hardware, serving as a robust form of two-factor security. By combining this hardware-backed identifier with “*something you know*" (e.g., user credentials) and "*something you are*" (e.g., biometric data), we can enhance privacy-focused encryption and authentication for outsourced data and industry-wide collaboration. Thinking about OpenRSP incorporating the secure identifier, an advanced framework that leverages state-of-the-art cryptographic techniques to address these challenges.

OpenRSP can incorporate two key innovations, Identity-Based Non-Interactive Key Exchange (IBNIKE) for Secure Identifier (SSID/ZKID) generation and Multi-Party Oblivious Transfers (MPOT) using Garbled Circuits for secure interactions within the RSP ecosystem. IBNIKE enables the generation of unique, privacy-preserving identifiers for end users without compromising their personal data. MPOT ensures secure collaboration between multiple entities involved in eSIM provisioning, safeguarding user privacy and system integrity.

OpenRSP represents a significant advancement in eSIM provisioning technology, offering a secure and privacy-preserving solution that meets the evolving needs of mobile network operators, device manufacturers, and end users. This draft will continue to improve and serve as a comprehensive guide for stakeholders interested in adopting OpenRSP to enhance the security and privacy of their eSIM ecosystems.

---
We will be providing a detailed analysis of the theory, implementation, challenges and potential benefits of incorporating these advanced cryptographic techniques into eSIM technology.
Our result will demonstrate that the proposed framework not only significantly improves the security and privacy of the RSP process but also lays the foundation for a more trustworthy and collaborative environment in the digital communication domain.

Work in progress . . .
