# ADCP Transport

> Defines the transport requirements and transport architecture of the AADA Device Coordination Protocol (ADCP).

---

# Document Information

| Field | Value |
|-------|-------|
| Protocol | ADCP |
| Document | Transport |
| Category | Protocol Specification |
| Document Type | Normative |
| Protocol Version | 1.x |
| Specification Version | 1.0 |
| Status | Stable and Actively Developed |
| Last Updated | 2026-07-19 |

---

# Purpose

This document defines the transport requirements of the AADA Device Coordination Protocol (ADCP).

ADCP is designed as a transport-independent application-layer protocol. Rather than defining a transport protocol, ADCP defines the minimum transport capabilities required for correct protocol operation.

---

# Scope

This document defines:

- Transport architecture.
- Required transport capabilities.
- Supported transport characteristics.
- Transport message model.
- Payload considerations.
- Session considerations.
- Transport conformance.

This document does **not** define:

- Discovery procedures.
- Authentication mechanisms.
- Message formats.
- MQTT topic hierarchy.
- Transport-specific implementation details.

Those topics are defined in their respective specifications.

---

# Requirement Language

The key words **"MUST"**, **"MUST NOT"**, **"REQUIRED"**, **"SHALL"**, **"SHALL NOT"**, **"SHOULD"**, **"SHOULD NOT"**, **"RECOMMENDED"**, **"NOT RECOMMENDED"**, **"MAY"**, and **"OPTIONAL"** are to be interpreted as described in RFC 2119.

---

# Definitions

| Term | Definition |
|------|------------|
| Transport | The underlying communication mechanism used to exchange ADCP messages. |
| Transport Message | A message transmitted by the underlying transport. |
| Protocol Message | A logical ADCP message defined by this specification. |
| Fragment | A transport message carrying part of a protocol message. |

---

# Table of Contents

1. Transport Architecture
2. Design Principles
3. Required Transport Capabilities
4. Transport Message Model
5. Payload Considerations
6. Session Considerations
7. Current Implementation
8. Conformance
9. Related Documents

---

# Transport Architecture

ADCP operates as an application-layer protocol above the underlying transport.

The protocol defines communication semantics independently of the transport used to deliver protocol messages.

A transport implementation is responsible for delivering protocol messages between participating entities.

---

# Design Principles

## Transport Independence

ADCP is designed independently of any specific transport protocol.

Protocol behavior SHALL remain independent of the transport implementation whenever practical.

---

## Embedded-First

Supported transports SHALL be suitable for resource-constrained embedded systems.

Transport implementations SHOULD minimize communication overhead while maintaining reliable protocol operation.

---

## Capability-Based Design

ADCP defines the capabilities required from a transport rather than requiring a specific transport protocol.

Multiple transport implementations MAY satisfy these requirements.

---

# Required Transport Capabilities

A transport used by ADCP SHALL provide, either natively or through an implementation layer, the following capabilities:

- Bidirectional communication.
- Reliable message delivery.
- Persistent connectivity where applicable.
- Efficient communication suitable for embedded devices.
- Support for structured message exchange.

In addition, transports SHOULD provide:

- Keep-alive mechanisms.
- Offline detection.
- Transport-level timeout handling.
- State synchronization capabilities, such as retained or snapshot-based message delivery.

---

# Transport Message Model

ADCP defines logical protocol messages.

A protocol message MAY be transported using one or more transport messages.

Where fragmentation is required, the implementation SHALL ensure that the receiving entity can reconstruct the complete protocol message before protocol processing begins.

Fragmentation mechanisms are transport-specific and are outside the scope of this specification.

---

# Payload Considerations

Transport implementations SHALL support payload sizes sufficient for ADCP protocol operation.

Implementations SHOULD define safe payload limits appropriate for available system resources.

Where transport payload limitations exist, implementations MAY fragment protocol messages into multiple transport messages.

The maximum payload size supported by an implementation SHALL be documented by that implementation.

---

# Session Considerations

ADCP MAY establish logical sessions between communicating entities.

Session management is protocol-dependent and may be used for purposes including:

- Authentication.
- Authorization.
- Message validation.
- Payload signing.
- Encryption.
- Session key management.

The definition of session behavior is provided by the applicable protocol mechanisms rather than the transport itself.

---

# Current Implementation

MQTT is the reference transport for the current ADCP implementation and is the only fully implemented transport at the time of this specification.

Current implementations make use of MQTT features including:

- Publish/Subscribe messaging.
- QoS.
- Keep Alive.
- Retained messages for state synchronization.

Future implementations MAY support additional transports provided they satisfy the transport requirements defined by this specification.

---

# Conformance

An implementation claiming compliance with ADCP SHALL use a transport that satisfies the mandatory transport capabilities defined in this document.

The choice of transport protocol is implementation-specific provided protocol interoperability is maintained.

---

# Related Documents

## Normative References

- [Overview](Overview.md)
- [Discovery](Discovery.md)
- [Authentication](Authentication.md)
- [Messages](Messages.md)

## Informative References

- [ADCP README](README.md)
- [Protocol Stack](../../architecture/ProtocolStack.md)

---

# Document Navigation

**Previous**

- [Overview](Overview.md)

**Next**

- [Discovery](Discovery.md)