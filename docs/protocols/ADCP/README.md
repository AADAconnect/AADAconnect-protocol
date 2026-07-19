# AADA Device Coordination Protocol (ADCP)

> The official specification of the AADA Device Coordination Protocol (ADCP).

---

# Document Information

| Field | Value |
|-------|-------|
| Protocol | ADCP |
| Document | README |
| Category | Protocol Specification |
| Document Type | Informative |
| Protocol Status | Stable and Actively Developed |
| Current Protocol Version | 1.x |
| Specification Version | 1.0 |
| Last Updated | 2026-07-18 |

---

# Overview

The **AADA Device Coordination Protocol (ADCP)** is the primary application-layer coordination protocol of the AADAconnect Platform.

ADCP enables trusted entities within the AADAconnect ecosystem to discover, identify, authenticate, authorize, provision, monitor, manage, and coordinate edge-native IoT devices through standardized JSON-based protocol messages exchanged over supported message-oriented transports.

Rather than defining device-specific behavior, ADCP defines a common language for communication between dashboards, devices, controllers, services, and other participating entities.

---

# Purpose

The purpose of ADCP is to provide a standardized protocol for exchanging structured information and coordinating device behavior throughout the AADAconnect Platform.

The protocol provides mechanisms for:

- Device discovery.
- Device identification.
- Authentication.
- Authorization.
- Information exchange.
- State reporting.
- Query and response operations.
- Configuration management.
- Device coordination.
- Event reporting.
- Capability negotiation.
- OTA coordination.

ADCP is transport-independent and defines protocol behavior independently of the underlying communication medium.

---

# Protocol Position

Within the AADAconnect Protocol Suite, ADCP serves as the primary coordination protocol.

```text
Applications
        │
        ▼
ADCP
        │
        ▼
MQTT / Other Supported Transports
```

ADCP may also coordinate with other AADAconnect protocols, including:

- APOP (Provisioning)
- AOTA (Over-the-Air Updates)
- AADAcom (Device-to-device communication)

---

# Document Structure

The ADCP specification is divided into focused documents.

| Document | Description |
|----------|-------------|
| Overview.md | Protocol architecture, scope, terminology, and design goals. |
| Transport.md | Supported transports and transport requirements. |
| Discovery.md | Device discovery mechanisms. |
| Authentication.md | Authentication, authorization, trust establishment, and security mechanisms. |
| Messages.md | Protocol message definitions and message categories. |
| DeviceInfo.md | Device information model and capability reporting. |
| OTA.md | Interaction between ADCP and AOTA. |
| Errors.md | Error model and protocol error definitions. |
| Timing.md | Timing requirements and protocol timeouts. |
| StateMachine.md | Protocol state machine and session behavior. |
| VersionHistory.md | Protocol revision history. |

---

# Design Goals

ADCP is designed to be:

- Embedded-first.
- Edge-native.
- Transport-independent.
- Message-oriented.
- Extensible.
- Modular.
- Secure by design.
- Backward compatible where practical.
- Efficient for resource-constrained devices.
- Suitable for long-term protocol evolution.

---

# Current Implementation

ADCP is currently the most mature protocol within the AADAconnect Protocol Suite and serves as the foundation for device coordination throughout the platform.

The protocol continues to evolve alongside the AADAconnect firmware and dashboard implementations.

Some related protocols, including APOP and AOTA, currently integrate with ADCP while continuing to mature independently.

---

# Specification Status

This repository documents the current ADCP specification implemented by the AADAconnect Platform.

As the protocol evolves, the specification is updated to accurately reflect implemented behavior while also defining the long-term architectural direction of the protocol.

---

# Related Documents

## Architecture

- [Architecture Overview](../../architecture/Overview.md)
- [Protocol Stack](../../architecture/ProtocolStack.md)
- [Versioning](../../architecture/Versioning.md)
- [Compatibility](../../architecture/Compatibility.md)
- [Security Model](../../architecture/SecurityModel.md)

## Related Protocols

- [APOP](../APOP/README.md)
- [AOTA](../AOTA/README.md)
- [AADAcom](../AADAcom/README.md)

# Conformance

Implementations claiming support for ADCP SHALL conform to the normative requirements defined throughout the ADCP specification.

This README is informative and does not define protocol requirements.

---

# Document Navigation

**Previous**

- [AADAconnect Protocol Suite](../../../README.md)

**Next**

- [ADCP Overview](Overview.md)