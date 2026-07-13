# AADAconnect Protocol Suite

> **Official protocol specifications for the AADAconnect platform.**

The **AADAconnect Protocol Suite** defines the communication protocols that power the AADAconnect platform. It specifies how AADAconnect-enabled devices, applications, dashboards, and network services communicate with one another through standardized, versioned, and interoperable protocols.

The protocol suite is designed with an **edge-native** philosophy where devices remain the primary source of truth for their operational state and control. Unlike traditional cloud-centric IoT systems, AADAconnect does not require centralized cloud infrastructure to function. Cloud services may extend functionality when available but are not fundamental to the architecture.

Designed from an embedded-first perspective, the protocol suite targets resource-constrained devices while providing a scalable foundation for secure device provisioning, remote management, firmware updates, device synchronization, and future protocol extensions.

---

# Protocol Suite

The AADAconnect Protocol Suite currently consists of the following protocols.

| Protocol | Description | Status |
|----------|-------------|--------|
| **ADCP** | AADA Device Control Protocol for device management, monitoring, configuration, telemetry and remote control. | Stable |
| **APOP** | AADA Provisioning Protocol used during initial device onboarding and network provisioning. | Under Development |
| **AOTA** | AADA Over-the-Air firmware update protocol. | Under Development |
| **AADAcom** | High-performance embedded communication protocol for direct device-to-device communication. | Experimental |
| **AADAnetSync** | Synchronization protocol used by AADAcom for distributed timing and coordination. | Experimental |

---

# Design Goals

The protocol suite is designed around the following principles.

- Edge-native architecture
- Embedded-first design
- Device-first control model
- User ownership of device data
- Modular protocol architecture
- Optional cloud integration
- Practical backward compatibility
- Versioned protocol evolution
- Security-conscious design
- Resource-efficient implementation

---

# Repository Structure

```
aadaconnect-protocol/
│
├── README.md
├── CHANGELOG.md
├── CONTRIBUTING.md
├── LICENSE
│
├── docs/
│   │
│   ├── architecture/
│   │   ├── Overview.md
│   │   ├── ProtocolStack.md
│   │   ├── NamingConvention.md
│   │   ├── Versioning.md
│   │   ├── Compatibility.md
│   │   └── SecurityModel.md
│   │
│   ├── protocols/
│   │   │
│   │   ├── ADCP/
│   │   │   ├── README.md
│   │   │   ├── Overview.md
│   │   │   ├── Transport.md
│   │   │   ├── Discovery.md
│   │   │   ├── Authentication.md
│   │   │   ├── Messages.md
│   │   │   ├── DeviceInfo.md
│   │   │   ├── OTA.md
│   │   │   ├── Errors.md
│   │   │   ├── Timing.md
│   │   │   ├── StateMachine.md
│   │   │   └── VersionHistory.md
│   │   │
│   │   ├── AADAcom/
│   │   │   ├── README.md
│   │   │   ├── Overview.md
│   │   │   ├── Mesh.md
│   │   │   ├── Discovery.md
│   │   │   ├── LeaderElection.md
│   │   │   ├── AudioTransport.md
│   │   │   ├── Synchronization.md
│   │   │   ├── ControlMessages.md
│   │   │   ├── Timing.md
│   │   │   ├── Errors.md
│   │   │   └── VersionHistory.md
│   │   │
│   │   ├── APOP/
│   │   │   ├── README.md
│   │   │   ├── ProvisioningFlow.md
│   │   │   ├── Security.md
│   │   │   └── VersionHistory.md
│   │   │
│   │   └── AOTA/
│   │
│   ├── schemas/
│   │   ├── adcp/
│   │   ├── aadacom/
│   │   ├── provisioning/
│   │   └── ota/
│   │
│   └── examples/
│       ├── MQTTExamples.md
│       ├── SpeakerExamples.md
│       └── ProvisioningExamples.md
│
└── assets/
    ├── diagrams/
    └── images/
```

---

# Documentation Scope

This repository contains the official specification of the AADAconnect Protocol Suite.

The documentation describes protocol behavior, message formats, timing requirements, state machines, interoperability rules, compatibility expectations, and version history.

Implementation details such as firmware architecture, FreeRTOS tasks, queues, source code organization, and internal module interactions are intentionally excluded and belong in the respective firmware repositories.

Each protocol specification documents the behavior implemented for that protocol version. Experimental functionality and planned extensions are explicitly identified and are not considered part of the normative specification until officially released.

---

# Intended Audience

This repository is intended for:

- Firmware developers
- Dashboard developers
- Mobile application developers
- Protocol implementers
- Contributors
- System integrators

---

# Versioning

Every protocol within the AADAconnect Protocol Suite is independently versioned. Changes that affect interoperability, message formats, protocol behavior, or compatibility are documented in the corresponding protocol specification and version history.

---

# License

See the `LICENSE` file for licensing information.