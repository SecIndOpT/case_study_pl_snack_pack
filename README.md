# A Survey on Life-Cycle-Oriented Certificate Management in Industrial Networking Environments

Reference: Goeppert J., Walz A., Sikora A. (2024) A Survey on Life-Cycle-Oriented Certificate Management in Industrial Networking Environments. *J. Sens. Actuator Netw. 13*(2), 26. [https://doi.org/10.3390/jsan13020026](https://doi.org/10.3390/jsan13020026)


In the past, OT and IT were strictly separated through hierarchical gateways. With the increasing demand for connectivity, the convergence of OT and IT is inevitable. This on one hand leads to an adoption of common Internet standards in OT networks but also to an increased attack surface OT networks are facing nowadays. A security measure to counteract these new threats is a *defense-in-depth* approach, which includes the need for cryptographic protection of industrial communications and devices. More precise, we need a way to guarantee integrity and authenticity of field devices, which leads to the requirements of certificates, a certificate-based mutually authenticated key agreement procedure, private keys and trust anchors in and for industrial end devices as well as secure management of these assets. The paper collects and elaborates different employed and proposed solutions stemming from reasearch, industrial protocols and protocols which stem from the IT-domain but find application in OT.

Some nomenclature:

- **End entity (EE):** Subject of the certificate management process (in our case, the field devices).
- **Certification authority (CA):** Entity that issues certificates and certification revocation information. CAs can have a hierarchical structure. The top-most CA (root CA) thus needs to utilize self-signed certificates. 
- **Registration Authority (RA):** Entity to which a CA delegates certain certificate management tasks (example tasks: authentication of EEs prior to certificate issuance by CA, archival of key pairs, revocation reporting)

## Certificate Management

We have different general concepts which describe how to equip an EE with certificates:

1. EE gets equipped with credentials at manufacturing time. At installation time, these credentials can be used to secure the integration of the device into the facility and the issuance of certificates.

1. Utilization of special protocols in order to equip EEs with certificates, without the need for pre-installed credentials.

1. Integration and/or adaptation of IT domain protocols to establish communication and security relation between CA and EEs. This enables the use of existing infrastructure for certificate management.

1. Pull architecture: EEs maintain a *Certificate Management Object* (CMO) that manages certificates. The CMO can also be managed by a commissioning application. The EE *pulls* the certificate from the CA.

1. Push architecture: We have a *Security Infrastructure Handler* (SIH) which can push certificates, private keys and trust anchors to system components. The EE itself can be allowed to generate private keys as well as posting *Certificate Signing Requests* (CSR) to the SIH. The SIH can be integrated into the CA or a dedicated entity.

## Entity Reference Architectures

The different approaches collected by the authors can be summarized to employing one of the following three entity reference architectures:

![Figure 6 from the original paper](./architectures.png)

1. We have a direct connection between field devices and the managing entity. This implies that both the EE and the managing entity provide common protocol mechanisms to manage certificates. Additionally, the managing entity must be able to issue trust anchors and certificates hence incorporating the functionallity of a CA. The managing entity can also be subdivided, for example into a CA that issues certifcates, a registration authority (RA) that verifies certificate management requests and a validation authority (VA) that validates certificates.

1. The second architecture involves and intermediary entity which acts as the direct communication partner for the EEs. For example, it can translate between protocols or execute required certificate management tasks like generating key pairs or imprinting signed certificates. With an architecture like this, the CA can be embedded into further security infrastructure, which might also contain an RA and/or VA. Furthermore, the CA and EE loose the need to implement a common protocol.

1. The last architecture is cluster-based and uses blockchains. Multiple EEs dynamically form a cluster with one cluster head. The cluster heads act as CAs that participate in the blockchain network which shares information about the member nodes' behaviour. This member behaviour defines, whether or not a certificate gets issued. Alternatively, the EEs could also employ self-signed certificates and let local RAs validate the identity binding through the Ethereum blockchain, using it as a global notary of certificates.

## Certificate Management Functions

## Product Life Cycle Stages







 