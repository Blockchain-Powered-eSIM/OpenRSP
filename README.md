# OpenRSP
OpenRSP is aiming to become a modern [Remote SIM Provisioning](https://github.com/Blockchain-Powered-eSIM/eSIM-Wallet/wiki/Remote-SIM-Provisioning) protocol, focusing on data integrity using modern cryptography , secure-by-design principle to deliver a trustless system in telecom industry which connects everyone around the globe.

### The issue with current [RSP](https://en.wikipedia.org/wiki/Remote_SIM_provisioning)
>
>The current RSP standard that remotely provision eSIM to user devie is based on a mechanism which revolves around exchanging keys and signing certificates between the device and the mobile >network operator (MNO). These keys and certificates are used to verify the authenticity of the device and establish a secure and encrypted connection.
>And the security relies on trusted parties, The device manufacturers here play a crucial role along with OS to make sure not reveal eSIM profile.
>This also makes the environment restricted and later a closed industry.
>>

### Resolved Issue
*With the [open source eSIM Smart Wallet](https://github.com/Blockchain-Powered-eSIM/smart-contract-suite) we have removed the issue that gets introduced in the eSIM stack based on current RSP which is*
>
>The right of independent service providers to transmit commands of loading profiles to SIM-cards in the device has been amended and the possibility to store arrays of profiles in independent certified data centres (Subscriptions manager) has appeared.
>

#### Where eSIM Smart Wallet allows users to own their profiles and remove the requirements to store profiles in data centres.
---

# Abstract

In the rapidly evolving field of digital wireless communication, ensuring robust security mechanisms within protocols and functions has become essential. The principle of "security by design" guides the development of trustworthy systems. 

**Open Source Remote SIM Provisioning (OpenRSP)** systems should inherit the secure and efficient activation of embedded SIMs (eSIMs) in a variety of devices from traditional RSP and utilise modern cryptography for data integrity resulting in trustworthy systems by removing trusted parties involved in the system.

Recent advancements in cryptographic techniques have significantly enhanced both the security and efficiency of these systems.

Exploring the application of state-of-the-art cryptography, including Zero-Knowledge Proofs (ZKP) and garbled circuits, to develop a highly secure, privacy focused and trustworthy RSP framework.

Designing this with the motivation of incorporating ZKP for device and user authentication, ensuring that authentication can be performed without revealing sensitive information to establish a secure handshake for network access. This method leverages the properties of ZKP to maintain privacy while proving possession of valid credentials. Additionally, garbled circuits are employed to secure profile management operations, allowing encrypted data to be processed without exposing it, thus ensuring end-to-end confidentiality.

We address the key management challenge through Identity-Based Cryptography (IBC). By using identities as public keys, IBC simplifies the key distribution process and enhances security. This framework is designed to be open-source, promoting collaboration among various stakeholders in the ecosystem and fostering innovation and interoperability.

We will be providing a detailed analysis of the theory, implementation, challenges and potential benefits of incorporating these advanced cryptographic techniques into eSIM technology.

Our result will demonstrate that the proposed framework not only significantly improves the security and privacy of the RSP process but also lays the foundation for a more trustworthy and collaborative environment in the digital communication domain.

---

### One of the approach

It includes modern authentication for eSIMs, ensuring their validity and enabling users to prove ownership of eSIM profiles to network providers without compromising their private credentials. One key aspect of our approach is the utilization of the eUICC unique identifier (EID) to create a Secure Identifier (SSID/ZKID/DID). The EID is inherently unique and tied to the device's hardware, serving as a robust form of two-factor security. By combining this hardware-backed identifier with “*something you know*" (e.g., user credentials) and "*something you are*" (e.g., biometric data), we can enhance privacy-focused encryption and authentication for outsourced data and industry-wide collaboration. Thinking about OpenRSP incorporating the secure identifier, an advanced framework that leverages state-of-the-art cryptographic techniques to address these challenges.

OpenRSP can incorporate two key innovations, Identity-Based Non-Interactive Key Exchange (IBNIKE) for Secure Identifier (SSID/ZKID) generation and Multi-Party Oblivious Transfers (MPOT) using Garbled Circuits for secure interactions within the RSP ecosystem. IBNIKE enables the generation of unique, privacy-preserving identifiers for end users without compromising their personal data. MPOT ensures secure collaboration between multiple entities involved in eSIM provisioning, safeguarding user privacy and system integrity.

OpenRSP represents a significant advancement in eSIM provisioning technology, offering a secure and privacy-preserving solution that meets the evolving needs of mobile network operators, device manufacturers, and end users. This draft will continue to improve and serve as a comprehensive guide for stakeholders interested in adopting OpenRSP to enhance the security and privacy of their eSIM ecosystems.

---

Work in progress . . .
