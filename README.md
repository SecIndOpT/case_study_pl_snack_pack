# A Survey on Life-Cycle-Oriented Certificate Management in Industrial Networking Environments

Reference: Goeppert J., Walz A., Sikora A. (2024) A Survey on Life-Cycle-Oriented Certificate Management in Industrial Networking Environments. *J. Sens. Actuator Netw. 13*(2), 26. [https://doi.org/10.3390/jsan13020026](https://doi.org/10.3390/jsan13020026)

<!-- TODO Remove this -->
> I don't know how we want to encorporate a good structure into this whole thing... Just following the structure of the paper kinda sucks but otherwise it tends to get pretty messy. Do you guys have an idea?


In the past, OT and IT were strictly separated through hierarchical gateways. With the increasing demand for connectivity, the convergence of OT and IT is inevitable. This on one hand leads to an adoption of common Internet standards in OT networks but also to an increased attack surface OT networks are facing nowadays. A security measure to counteract these new threats is a *defense-in-depth* approach, which includes the need for cryptographic protection of industrial communications and devices. More precise, we need a way to guarantee integrity and authenticity of field devices, which leads to the requirements of certificates, a certificate-based mutually authenticated key agreement procedure, private keys and trust anchors in and for industrial end devices as well as secure management of these assets.

Some nomenclature:

- **End entity (EE):** Subject of the certificate management process (in our case, the field devices).
- **Certification authority (CA):** Entity that issues certificates and certification revocation information. CAs can have a hierarchical structure. The top-most CA (root CA) thus needs to utilize self-signed certificates. 
- **Registration Authority (RA):** Entity to which a CA delegates certain certificate management tasks (example tasks: authentication of EEs prior to certificate issuance by CA, archival of key pairs, revocation reporting)

## Academic Certificate Management Approaches

- EE gets equipped with credentials at manufacturing time. At installation time, the onboarding process and issuance of certificates can then be secured by using these credentials.
- Usage of special protocols to equip devices with certificates, without the need for pre-installed certificates on the device.
- Integration of PKI in operator's domain (no focus on secure onboarding)
- Mechanisms to enable PKIs for low-resource EEs (special protocols, certificate profiles)
- Usage of certificate whitelists as an additional asset

## Certificate Management Approaches from Industrial Communication Standards

### EtherNet/IP with Common Industrial Protocol (CIP) Security

End-device maintains a *Certificate Management Object* (CMO) that manages X.509 certificates. The CMO is also manageable by a commissioning application. Usage of EST protocol for EE to pull certificates from CA.

### PROFINET

Utilization of *Security Infrastructure Handler* (SIH) which can push certificates, private keys and trust anchors to system components via PROFINET-native protocol. Additionally, EE itself is allowed to generate private keys and post *Certificate Signing Request* (CSR) to SIH. Like EtherNet/IP with CIP, PROFINET uses site-specific X.509 certificates.

### UPC UA

### Time Sensitive Networking (TSN) Profile (IEC/IEEE 60802)

Uses NETCONF/YANG over TLS to enable management of certificates, keys and trust anchors. Dedicated *TSN domain management entities* (TDME) in the role of NETCONF clients can push certificates, keys and trust anchors to EEs, which are NETCONF servers.

## Certificate Management Approaches stemming from IT-Originated Standards

Using IT domain protocols allows to use existing infrastructure for certificate management. 






 