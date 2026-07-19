# ADCP Discovery

> Defines how entities discover and synchronize platform state using Fetch Payloads within the AADA Device Coordination Protocol (ADCP).

---

# Document Information

| Field | Value |
|-------|-------|
| Protocol | ADCP |
| Document | Discovery |
| Category | Protocol Specification |
| Document Type | Normative |
| Protocol Version | 1.x |
| Specification Version | 1.0 |
| Status | Stable and Actively Developed |
| Last Updated | 2026-07-19 |

---

# Purpose

This document defines the discovery mechanism of the AADA Device Coordination Protocol (ADCP).

Unlike traditional discovery protocols that locate devices through network scanning or broadcast mechanisms, ADCP performs discovery by synchronizing authoritative platform state through retained Fetch Payloads.

This allows all participating entities to maintain a consistent view of devices and associated metadata within a User Scope.

---

# Scope

This document defines:

- Discovery architecture.
- Fetch Payload synchronization.
- Automatic device discovery.
- Discovery lifecycle.
- Discovery completion.
- Relationship between discovery and authentication.

This document does **not** define:

- Authentication procedures.
- Payload formats.
- Metadata structures.
- Compatibility negotiation.
- Transport-specific implementation details.

These topics are defined by their respective specifications.

---

# Requirement Language

The key words **"MUST"**, **"MUST NOT"**, **"REQUIRED"**, **"SHALL"**, **"SHALL NOT"**, **"SHOULD"**, **"SHOULD NOT"**, **"RECOMMENDED"**, **"NOT RECOMMENDED"**, **"MAY"**, and **"OPTIONAL"** are to be interpreted as described in RFC 2119.

---

# Definitions

This document uses the architectural terminology defined in the AADAconnect Architecture Overview.

Protocol-specific terms are introduced only where required.

---

# Table of Contents

1. Discovery Architecture
2. Discovery Model
3. Discovery Lifecycle
4. Fetch Payload Synchronization
5. Meta Payload Synchronization
6. Discovery Completion
7. Relationship with Authentication
8. Current Implementation
9. Conformance
10. Related Documents

---

# Discovery Architecture

ADCP discovery is based on synchronized platform state rather than network-level device discovery.

Participating entities discover devices by obtaining and processing authoritative Fetch Payloads maintained within the AADAconnect Platform.

Discovery therefore becomes a consequence of successful state synchronization rather than an independent protocol operation.

---

# Discovery Model

Discovery is passive.

Entities do not actively search the network for devices.

Instead, participating entities receive retained Fetch Payloads after connecting to the transport and subscribing to the required protocol topics.

The received Fetch Payload provides the current synchronized state of the User Scope.

Entities SHALL validate received Fetch Payloads before using the contained information.

---

# Discovery Lifecycle

A typical discovery sequence consists of:

```text
Power On
      │
Connect Network
      │
Connect Transport
      │
Subscribe
      │
Receive Retained Fetch Payload
      │
Validate Fetch Payload
      │
Locate Local Device Information
      │
───────────────┐
Found?         │
      │        │
     Yes      No
      │        │
Continue   Add Device
      │        │
      └────────┘
            │
Publish Updated Fetch Payload
            │
Platform Synchronized
```

Discovery SHALL occur automatically without requiring manual user interaction.

---

# Fetch Payload Synchronization

Fetch Payloads represent the authoritative synchronized state of a particular category of platform information.

Examples include:

- Device Fetch Payload.
- Future platform Fetch Payloads defined by subsequent protocol revisions.

Implementations SHALL validate a received Fetch Payload before processing its contents.

If validation succeeds, the receiving entity SHALL synchronize its local protocol state with the received Fetch Payload.

If the local entity determines that it is not represented within the synchronized Fetch Payload, it MAY update the authoritative Fetch Payload according to protocol requirements.

---

# Meta Payload Synchronization

Fetch Payloads MAY reference one or more Meta Payloads.

Meta Payloads separate frequently changing platform information from descriptive metadata.

Current examples include:

- Name Meta.
- Room Meta.

Future protocol revisions MAY define additional Meta Payloads, including:

- Capability Meta.
- Compatibility Meta.
- Security Meta.

Receiving entities SHALL synchronize referenced Meta Payloads as required for correct protocol operation.

---

# Discovery Completion

Discovery is considered complete when:

- The entity has received the required Fetch Payloads.
- Fetch Payload validation has completed successfully.
- Required Meta Payloads have been synchronized.
- The entity has established a consistent local view of the synchronized state of its User Scope.

Additional protocol stages, including authentication, compatibility negotiation, and operational communication, MAY follow discovery.

---

# Relationship with Authentication

Discovery does not replace authentication.

However, received Fetch Payloads participate in establishing protocol trust.

Implementations SHALL validate received Fetch Payloads according to the authentication and integrity requirements defined by the Authentication specification before accepting synchronized platform state.

Authentication requirements are defined separately by the ADCP Authentication specification.

---

# Current Implementation

The current ADCP implementation performs discovery using retained MQTT Fetch Payloads.

Upon connecting to the MQTT broker and subscribing to the required protocol topics, entities receive the retained Device Fetch Payload representing the current synchronized device list.

Entities determine whether they are already represented within the Fetch Payload.

If a newly connected device is not present, it creates or updates the authoritative Device Fetch Payload according to the protocol rules.

The current implementation also synchronizes Name Meta and Room Meta payloads.

---

# Conformance

An implementation claiming compliance with ADCP SHALL implement the discovery and synchronization principles defined by this specification.

Protocol-specific validation rules are defined by the Authentication specification.

---

# Related Documents

## Normative References

- [Overview](Overview.md)
- [Transport](Transport.md)
- [Authentication](Authentication.md)
- [Messages](Messages.md)
- [Device Information](DeviceInfo.md)

## Informative References

- [ADCP README](README.md)

---

# Document Navigation

**Previous**

- [Transport](Transport.md)

**Next**

- [Authentication](Authentication.md)