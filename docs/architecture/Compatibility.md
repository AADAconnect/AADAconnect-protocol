# Compatibility

> Defines the compatibility model used throughout the AADAconnect Protocol Suite.

---

# Document Information

| Field | Value |
|-------|-------|
| Document | Compatibility |
| Category | Architecture |
| Document Type | Normative |
| Applies To | AADAconnect Protocol Suite |
| Status | Stable |
| Version | 1.0 |
| Last Updated | 2026-07-14 |

---

# Purpose

This document defines how implementations determine protocol compatibility within the AADAconnect Protocol Suite.

Rather than relying solely on protocol version numbers, compatibility is determined using protocol-specific compatibility information exchanged between communicating implementations.

The objective is to maximize interoperability while ensuring incompatible implementations fail predictably with clear diagnostic information.

---

# Scope

This document defines:

- Compatibility principles.
- Version compatibility.
- Compatibility negotiation.
- Protocol Compatibility Profiles.
- Capability negotiation.
- Graceful degradation.

This document does **not** define protocol-specific compatibility messages or negotiation procedures. Those are defined by the respective protocol specifications.

---

# Requirement Language

The key words **"MUST"**, **"MUST NOT"**, **"REQUIRED"**, **"SHALL"**, **"SHALL NOT"**, **"SHOULD"**, **"SHOULD NOT"**, **"RECOMMENDED"**, **"NOT RECOMMENDED"**, **"MAY"**, and **"OPTIONAL"** are to be interpreted as described in RFC 2119.

---

# Definitions

| Term | Definition |
|------|------------|
| Compatibility | The ability of two implementations to communicate according to a protocol specification. |
| Compatibility Negotiation | The process of determining whether two implementations can communicate. |
| Protocol Compatibility Profile | Information describing the protocol support of an implementation. |
| Capability | An optional protocol feature supported by an implementation. |

---

# Table of Contents

1. Compatibility Philosophy
2. Compatibility Model
3. Protocol Compatibility Profile
4. Compatibility Negotiation
5. Capability Negotiation
6. Graceful Degradation
7. Current Implementation
8. Conformance
9. Related Documents

---

# Compatibility Philosophy

The AADAconnect Protocol Suite is designed to maximize interoperability between implementations while maintaining predictable protocol behavior.

Implementations SHOULD remain interoperable whenever practical.

When compatibility cannot be achieved, implementations SHALL fail gracefully and report the reason for incompatibility.

Users and applications SHOULD receive sufficient information to determine whether a firmware or software update is required.

---

# Compatibility Model

Protocol compatibility SHALL be determined using protocol-specific compatibility information.

Protocol version numbers alone SHALL NOT be used as the sole compatibility decision.

Each protocol specification defines:

- Compatibility rules.
- Compatibility data.
- Version compatibility.
- Feature compatibility.
- Extension compatibility.

---

# Protocol Compatibility Profile

Every implementation SHOULD expose a Protocol Compatibility Profile.

The Protocol Compatibility Profile MAY include:

- Supported protocols.
- Supported protocol versions.
- Compatibility information.
- Supported optional capabilities.
- Supported extensions.
- Implementation limitations.

Individual protocol specifications define how this information is represented and exchanged.

---

# Compatibility Negotiation

Compatibility SHALL be evaluated before normal protocol operation begins.

A successful negotiation SHALL determine:

- Supported protocol.
- Compatible protocol version.
- Supported capabilities.
- Optional protocol features.

If no compatible protocol version exists, the protocol session SHALL NOT be established.

The implementation SHALL report the compatibility failure.

---

# Capability Negotiation

Protocols MAY define optional capabilities.

Where capability negotiation exists, implementations SHALL advertise supported capabilities according to the protocol specification.

Unsupported optional capabilities SHALL NOT prevent communication when the remaining protocol behavior remains compatible.

---

# Graceful Degradation

When compatible protocol versions exist but optional capabilities differ, implementations SHOULD continue operating using the mutually supported feature set.

Unavailable capabilities SHOULD be clearly reported.

Implementations SHOULD avoid unnecessarily terminating otherwise compatible protocol sessions.

---

# Example

The following example illustrates compatibility negotiation during device onboarding.

```
Smart Plug
     │
     │ SoftAP
     ▼
Dashboard
     │
     │ HTTP + JSON (APOP)
     ▼
Retrieve Protocol Compatibility Profile
     │
     ├── ADCP Version
     ├── APOP Version
     ├── AOTA Version
     ├── Compatibility Information
     ├── Supported Capabilities
     └── Firmware Information
     │
     ▼
Compatibility Evaluation
     │
     ├── Compatible
     │      │
     │      ▼
     │ Continue Provisioning
     │
     └── Incompatible
            │
            ▼
 Report Compatibility Error
 Recommend Firmware Upgrade
```

This example is informative.

Individual protocol specifications define the exact negotiation procedure.

---

# Current Implementation

In the current AADAconnect implementation, compatibility negotiation primarily occurs during device provisioning using APOP.

Future protocols may perform additional compatibility negotiation where appropriate.

---

# Conformance

An implementation claiming compliance with the AADAconnect Protocol Suite SHALL implement the compatibility principles defined in this document.

Protocols SHALL define their own compatibility rules in accordance with this specification.

---

# Related Documents

## Normative References

- [Versioning](Versioning.md)

## Informative References

- [Architecture Overview](Overview.md)
- [Protocol Stack](ProtocolStack.md)

---

# Document Navigation

**Previous:** [Versioning](Versioning.md)

**Next:** [SecurityModel](SecurityModel.md)