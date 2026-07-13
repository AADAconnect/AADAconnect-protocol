# Architecture Overview

## Purpose

The AADAconnect Protocol Suite defines the communication architecture used by the AADAconnect platform. Rather than being a single protocol, it consists of multiple independent protocols, each designed to solve a specific communication problem while operating together as a unified protocol suite.

This document provides a high-level overview of the protocol architecture, the responsibilities of each protocol, and how they interact within the AADAconnect ecosystem.

---

# Architecture Philosophy

The AADAconnect Protocol Suite is designed around the following architectural principles:

- **Edge-Native** – Devices remain the authoritative source of their operational state and control.
- **Embedded-First** – Protocols are designed for resource-constrained embedded systems from the outset.
- **Modular** – Each protocol has a clearly defined responsibility and can evolve independently.
- **Extensible** – New protocols and protocol revisions can be introduced without redesigning the entire ecosystem.
- **Versioned** – Every protocol is independently versioned to allow controlled evolution.
- **Transport-Aware** – Protocols are designed for their intended transport while remaining adaptable where practical.
- **Security-Conscious** – Security is considered throughout protocol design without unnecessarily increasing implementation complexity.

---

# Protocol Hierarchy

The AADAconnect Protocol Suite currently consists of the following protocols.

```
AADAconnect Platform
│
├── AADAconnect Protocol Suite
│   │
│   ├── ADCP
│   │   ├── APOP
│   │   └── AOTA
│   │
│   └── AADAcom
│       └── AADAnetSync
│
├── Firmware
├── Dashboard / Applications
└── Optional Network Services
```

Each protocol is responsible for a specific area of communication and interoperability.

---

# Protocol Responsibilities

## ADCP

The AADA Device Coordination Protocol (ADCP) is the primary protocol used for communication between AADAconnect-enabled devices and management applications.

Its responsibilities include:

- Device management
- Device monitoring
- Remote control
- Configuration
- Device information exchange
- Telemetry
- Command processing

ADCP serves as the foundation for most AADAconnect-enabled devices.

---

## APOP

The AADA Provisioning Protocol (APOP) defines the onboarding process for compatible devices.

Typical responsibilities include:

- Initial device provisioning
- Network configuration
- Device registration
- Secure transfer of configuration parameters

APOP operates as part of the ADCP ecosystem.

---

## AOTA

The AADA Over-the-Air Protocol (AOTA) defines the firmware update process used by compatible devices.

Its responsibilities include:

- Firmware update initiation
- Update progress reporting
- Firmware validation
- Update completion reporting
- Error reporting during update

AOTA is integrated with ADCP.

---

## AADAcom

AADAcom is an embedded communication protocol designed for direct communication between AADAconnect devices.

Unlike ADCP, which focuses on device management, AADAcom is intended for low-latency, high-performance communication between devices.

Typical applications include:

- Distributed audio systems
- Multi-device coordination
- Real-time communication
- Future embedded networking applications

---

## AADAnetSync

AADAnetSync is a synchronization protocol used within AADAcom.

Its primary responsibility is maintaining synchronized operation across participating devices.

It is not intended for standalone use.

---

# Protocol Relationships

Although each protocol has an independent specification, they are designed to complement one another.

For example:

- A device may be provisioned using **APOP**.
- Once provisioned, it is managed through **ADCP**.
- Firmware updates are performed using **AOTA**.
- Multiple devices may communicate directly using **AADAcom**.
- Distributed synchronization within AADAcom is provided by **AADAnetSync**.

Not every device is required to implement every protocol.

---

# Implementation Model

The protocol specifications describe communication behavior and interoperability requirements.

Individual firmware implementations are free to organize their internal software architecture as appropriate, provided externally observable protocol behavior remains compliant with the corresponding specification.

This separation allows different implementations to remain interoperable while using different internal architectures.

---

# Scope

This document provides only a high-level architectural overview.

Detailed specifications for each protocol are provided within their respective documentation directories.

```
docs/protocols/

├── ADCP/
├── APOP/
├── AOTA/
└── AADAcom/
```

---

# Related Documents

- ProtocolStack.md
- NamingConvention.md
- Versioning.md
- Compatibility.md
- SecurityModel.md