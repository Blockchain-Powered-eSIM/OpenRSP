# Certificate Issuer [SGP.22 - RSP Technical Specification v2.6](https://www.gsma.com/solutions-and-impact/technologies/esim/wp-content/uploads/2024/09/SGP.22-v2.6.pdf)

A Certificate Issuer issues certificates for Remote SIM Provisioning system entities and acts as a trusted root for the purpose of authentication of the entities of the system. The specification supports X.509 certificate format.  

The following certificates SHALL be signed and issued by a GSMA CI:
- GSMA CI Certificate (CERT.CI.ECDSA)
- EUM Certificates (CERT.EUM.ECDSA)
- SM-DP+ Certificate (CERT.DPauth.ECDSA and CERT.DPpb.ECDSA)
- SM-DP+ TLS Certificate (CERT.DP.TLS)
- SM-DS Certificate (CERT.DSauth.ECDSA)
- SM-DS TLS Certificate (CERT.DS.TLS)

The following certificate SHALL be signed and issued by the EUM:
- eUICC Certificate (CERT.EUICC.ECDSA)

Even though each eUICC SHALL support at least two sets of elliptic curve parameters, which can be chosen from by an RSP server for its signatures and ECKA, an eUICC SHALL have at least one CERT.EUICC.ECDSA.

<img width="797" alt="Screenshot 2024-10-14 at 8 11 53 PM" src="https://github.com/user-attachments/assets/8bf34235-7ff1-4fde-aec0-3a2261e6e769">

The Algorithm Identifiers of all certificates of a certificate chain SHALL point to the same curve.
- The SM-DP+ has 2 ECDSA Certificates (CERT.DPauth.ECDSA and CERT.DPpb.ECDSA).
- The CERT.DPauth.ECDSA is used for authentication to the eUICC, and the CERT.DPpb.ECDSA is used for Profile binding.
- The certificates CERT.CI.ECDSA, CERT.EUICC.ECDSA, CERT.EUM.ECDSA, CERT.DPauth.ECDSA, CERT.DPpb.ECDSA, CERT.DP.TLS, CERT.DSauth.ECDSA, and CERT.DS.TLS exchanged over ES9+, ES10b, ES8+ and ES11 are described in the next sections.
