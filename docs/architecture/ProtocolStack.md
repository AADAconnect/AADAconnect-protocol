# Protocol Stack

> Defines the layered architecture of the AADAconnect Protocol Suite and the responsibilities of each architectural layer.

---

# Document Information

| Field | Value |
|-------|-------|
| Document | Protocol Stack |
| Category | Architecture |
| Document Type | Normative |
| Applies To | AADAconnect Protocol Suite |
| Status | Draft |
| Version | 1.0 |
| Last Updated | 2026-07-14 |

---

# Purpose

This document defines the layered architecture of the AADAconnect Protocol Suite.

It identifies the responsibilities of each architectural layer, distinguishes AADAconnect protocols from the transport technologies they use, and establishes how applications, protocols, transports, and networks interact.

All protocol specifications within the AADAconnect Protocol Suite SHALL conform to the architectural model defined in this document.

---

# Scope

This document defines:

- The architectural layers of the AADAconnect Protocol Suite.
- The responsibilities of each layer.
- The relationship between protocols and transport technologies.
- The role of each protocol within the protocol suite.

This document does **not** define:

- Protocol message formats.
- Authentication mechanisms.
- Device state machines.
- Packet structures.
- Transport-specific implementation details.

These topics are specified within the respective protocol specifications.

---

# Requirement Language

The key words **"MUST"**, **"MUST NOT"**, **"REQUIRED"**, **"SHALL"**, **"SHALL NOT"**, **"SHOULD"**, **"SHOULD NOT"**, **"RECOMMENDED"**, **"NOT RECOMMENDED"**, **"MAY"**, and **"OPTIONAL"** in this specification are to be interpreted as described in RFC 2119.

---

# Table of Contents

1. Architectural Overview
2. Layered Architecture
3. Application Layer
4. Protocol Layer
5. Transport Layer
6. Network Layer
7. Protocol Responsibilities
8. Current Protocol Stack
9. Related Documents

---

# Architectural Overview

The AADAconnect Protocol Suite follows a layered architecture.

Each layer has a clearly defined responsibility and communicates only with the adjacent layers through well-defined interfaces.

Separating responsibilities into layers improves maintainability, allows protocols to evolve independently, and enables multiple transport technologies to be used without changing protocol behavior.

---

# Layered Architecture

```
Applications
│
├── Dashboard
├── Mobile Applications
├── Desktop Applications
├── Future SDKs
│
├────────────────────────────────────────────
│        AADAconnect Protocol Suite
│
├── ADCP
├── APOP
├── AOTA
├── AADAcom
│     └── AADAnetSync
│
├────────────────────────────────────────────
│
├── MQTT
├── HTTP
├── HTTPS
├── Wi-Fi Peer Communication (IEEE 802.11)
│
├────────────────────────────────────────────
│
├── Wi-Fi
├── Ethernet
├── Internet
└── Local Networks
```

---

# Application Layer

The Application Layer consists of software that interacts with AADAconnect devices using one or more protocols defined by this specification.

Examples include:

- Web dashboards
- Mobile applications
- Desktop applications
- SDKs
- Automation platforms
- Future third-party implementations

Applications SHOULD communicate through the protocol layer rather than interacting directly with transport technologies.

---

# Protocol Layer

The Protocol Layer defines the communication rules used by the AADAconnect ecosystem.

Protocols specify:

- Device behavior.
- Message formats.
- Operational workflows.
- Coordination mechanisms.
- Compatibility requirements.

Protocols are transport-independent wherever practical.

Individual protocol specifications define how each protocol maps onto supported transport technologies.

---

# Transport Layer

The Transport Layer carries protocol data between communicating endpoints.

Transport technologies are not part of the AADAconnect Protocol Suite.

Instead, they provide the communication channels used by AADAconnect protocols.

Current transports include:

| Transport | Used By |
|-----------|---------|
| MQTT | ADCP, AOTA |
| HTTP | APOP |
| HTTPS | AOTA |
| Wi-Fi Peer Communication | AADAcom |

Additional transports MAY be supported in future revisions provided they satisfy the requirements of the corresponding protocol.

---

# Network Layer

The Network Layer provides the underlying connectivity required by transport technologies.

Examples include:

- Wi-Fi
- Ethernet
- Internet
- Local IP networks

The protocol specifications generally do not depend on a specific network technology unless explicitly stated.

---

# Protocol Responsibilities

Each protocol within the AADAconnect Protocol Suite has a clearly defined responsibility.

| Protocol | Primary Responsibility |
|----------|-------------------------|
| ADCP | Device coordination, management, monitoring, and remote control. |
| APOP | Device provisioning and onboarding. |
| AOTA | Firmware update management. |
| AADAcom | Embedded device-to-device communication. |
| AADAnetSync | Time synchronization and coordination within AADAcom. |

Protocols SHOULD avoid overlapping responsibilities whenever practical.

---

# Current Protocol Stack

The current protocol relationships are summarized below.

- ADCP provides device coordination and operational communication.
- APOP is an independent provisioning protocol using SoftAP, HTTP, and JSON.
- AOTA is an independent firmware update protocol that uses ADCP for update coordination and HTTPS for firmware delivery.
- AADAcom provides embedded peer-to-peer communication between compatible devices.
- AADAnetSync is a synchronization sub-protocol within AADAcom.

### Current Implementation

The official AADAconnect firmware currently implements APOP and AOTA functionality within the ADCP firmware module.

This implementation detail does not change their status as independent protocols within the AADAconnect Protocol Suite specification.

Future firmware revisions MAY separate these implementations without affecting protocol compatibility.

---

# Related Documents

## Normative References

- [Versioning](Versioning.md)
- [Compatibility](Compatibility.md)
- [Security Model](SecurityModel.md)

## Informative References

- [Architecture Overview](Overview.md)

---

# Document Navigation

**Previous:** [Architecture Overview](Overview.md)

**Next:** [Versioning](Versioning.md)