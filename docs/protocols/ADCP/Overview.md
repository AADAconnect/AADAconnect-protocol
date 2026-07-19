# ADCP Overview

> Defines the purpose, scope, architectural role, and design principles of the AADA Device Coordination Protocol (ADCP).

---

# Document Information

| Field | Value |
|-------|-------|
| Protocol | ADCP |
| Document | Overview |
| Category | Protocol Specification |
| Document Type | Normative |
| Protocol Version | 1.x |
| Specification Version | 1.0 |
| Status | Stable and Actively Developed |
| Last Updated | 2026-07-19 |

---

# Purpose

The AADA Device Coordination Protocol (ADCP) is the primary application-layer coordination protocol of the AADAconnect Platform.

ADCP provides a standardized mechanism for trusted entities to exchange structured information and coordinate device behavior throughout the AADAconnect ecosystem.

The protocol enables entities to discover, identify, authenticate, authorize, provision, monitor, configure, manage, query, and coordinate devices through standardized JSON-based protocol messages exchanged over supported message-oriented transports.

---

# Scope

This document defines:

- The purpose of ADCP.
- The architectural role of ADCP.
- Protocol scope.
- Design goals.
- Design principles.
- Protocol entities.
- Operational model.
- Relationship to other AADAconnect protocols.

This document does **not** define:

- Transport-specific behavior.
- Authentication mechanisms.
- Message formats.
- Device information structures.
- Timing requirements.
- Error handling procedures.

Those topics are defined by their respective specification documents.

---

# Requirement Language

The key words **"MUST"**, **"MUST NOT"**, **"REQUIRED"**, **"SHALL"**, **"SHALL NOT"**, **"SHOULD"**, **"SHOULD NOT"**, **"RECOMMENDED"**, **"NOT RECOMMENDED"**, **"MAY"**, and **"OPTIONAL"** are to be interpreted as described in RFC 2119.

---

# Definitions

| Term | Definition |
|------|------------|
| Entity | Any participant capable of communicating using ADCP. |
| Coordination | The exchange of protocol messages to establish, maintain, or modify the operational state of devices and services. |
| Protocol Message | A structured JSON message defined by the ADCP specification. |

---

# Table of Contents

1. Architectural Role
2. Protocol Scope
3. Design Goals
4. Design Principles
5. Protocol Entities
6. Operational Model
7. Relationship to Other Protocols
8. Conformance
9. Related Documents

---

# Architectural Role

ADCP serves as the primary coordination protocol within the AADAconnect Protocol Suite.

Rather than defining device-specific behavior, ADCP defines a standardized language through which participating entities exchange information, coordinate operations, and manage device state.

ADCP is independent of any specific device category and is intended to support a wide range of embedded systems deployed within the AADAconnect Platform.

---

# Protocol Scope

ADCP provides standardized mechanisms for:

- Device discovery.
- Device identification.
- Authentication.
- Authorization.
- Information exchange.
- Query and response operations.
- Configuration management.
- Device management.
- State reporting.
- Event reporting.
- Capability negotiation.
- OTA coordination.
- Compatibility negotiation.

ADCP intentionally separates protocol behavior from application-specific logic.

The protocol defines **how** entities communicate rather than **what** individual devices are required to do.

---

# Design Goals

The design goals of ADCP are:

- Embedded-first architecture.
- Edge-native operation.
- Transport independence.
- JSON-based interoperability.
- Message-oriented communication.
- Modular protocol design.
- Extensibility.
- Secure-by-design architecture.
- Efficient operation on resource-constrained devices.
- Long-term protocol evolution.
- Backward compatibility where practical.

---

# Design Principles

ADCP is designed according to the following principles:

## Standardized Communication

All participating entities communicate using standardized protocol messages defined by this specification.

---

## Separation of Responsibilities

Protocol behavior, transport behavior, security, and application logic remain separate concerns.

---

## Device-Centric Coordination

Devices are the primary operational entities of the AADAconnect Platform.

ADCP coordinates interactions with devices while allowing each device to remain authoritative for its own operational state.

---

## Transport Independence

ADCP defines protocol behavior independently of the underlying transport.

The protocol may operate over any transport capable of satisfying the requirements defined in the Transport specification.

---

## Extensibility

The protocol is designed to evolve through versioned extensions while maintaining compatibility wherever practical.

---

# Protocol Entities

An ADCP entity is any implementation capable of participating in ADCP communication.

Examples include:

- Devices.
- Dashboards.
- Mobile applications.
- Desktop applications.
- Embedded controllers.
- Services.
- Development tools.

Each entity performs responsibilities defined by the applicable protocol specification.

---

# Operational Model

ADCP follows a message-oriented coordination model.

Entities exchange structured protocol messages to:

- Request information.
- Report information.
- Request operations.
- Respond to requests.
- Report events.
- Synchronize state.
- Exchange capabilities.
- Coordinate device behavior.

The protocol defines the meaning and structure of these interactions independently of the transport used to deliver them.

---

# Relationship to Other Protocols

Within the AADAconnect Protocol Suite:

- **APOP** provides device provisioning.
- **AOTA** provides firmware update mechanisms.
- **AADAcom** provides peer-to-peer device communication.

ADCP coordinates operational communication throughout the platform and interoperates with these protocols where required.

---

# Conformance

An implementation claiming compliance with ADCP SHALL conform to the normative requirements defined throughout the ADCP specification.

---

# Related Documents

## Normative References

- [Transport](Transport.md)
- [Discovery](Discovery.md)
- [Authentication](Authentication.md)
- [Messages](Messages.md)
- [Device Information](DeviceInfo.md)
- [Errors](Errors.md)
- [Timing](Timing.md)
- [State Machine](StateMachine.md)

## Informative References

- [ADCP README](README.md)
- [Architecture Overview](../../architecture/Overview.md)
- [Protocol Stack](../../architecture/ProtocolStack.md)

---

# Document Navigation

**Previous**

- [ADCP README](README.md)

**Next**

- [Transport](Transport.md)