# Versioning

> Defines the versioning model for the AADAconnect Protocol Suite and its constituent protocols.

---

# Document Information

| Field | Value |
|-------|-------|
| Document | Versioning |
| Category | Architecture |
| Document Type | Normative |
| Applies To | AADAconnect Protocol Suite |
| Status | Stable |
| Version | 1.0 |
| Last Updated | 2026-07-14 |

---

# Purpose

This document defines the versioning strategy used throughout the AADAconnect Protocol Suite.

The protocol suite consists of multiple independent protocols that evolve at different rates. To support this, each protocol maintains its own version while the protocol suite itself also has a separate version identifying the overall specification release.

This document establishes the rules governing version assignment, compatibility expectations, and protocol evolution.

---

# Scope

This document defines:

- Protocol Suite versioning.
- Individual protocol versioning.
- Semantic version numbering.
- Compatibility expectations between versions.
- Version lifecycle principles.

This document does **not** define protocol-specific version fields or negotiation mechanisms. Those are defined by the respective protocol specifications.

---

# Requirement Language

The key words **"MUST"**, **"MUST NOT"**, **"REQUIRED"**, **"SHALL"**, **"SHALL NOT"**, **"SHOULD"**, **"SHOULD NOT"**, **"RECOMMENDED"**, **"NOT RECOMMENDED"**, **"MAY"**, and **"OPTIONAL"** in this specification are to be interpreted as described in RFC 2119.

---

# Definitions

For the purposes of this specification:

| Term | Definition |
|------|------------|
| Protocol Suite | The complete collection of protocols that constitute the AADAconnect Protocol Suite. |
| Protocol Version | The version assigned to an individual protocol. |
| Suite Version | The version assigned to the overall AADAconnect Protocol Suite specification. |
| Semantic Version | A version expressed as **MAJOR.MINOR.PATCH**. |
| Breaking Change | A change that may prevent interoperability with previous implementations. |

---

# Table of Contents

1. Versioning Model
2. Protocol Suite Version
3. Protocol Version
4. Semantic Versioning
5. Version Lifecycle
6. Compatibility Principles
7. Current Versioning Strategy
8. Conformance
9. Related Documents

---

# Versioning Model

The AADAconnect Protocol Suite uses two independent versioning levels:

1. **Protocol Suite Version**
2. **Individual Protocol Version**

Each protocol evolves independently and SHALL maintain its own version number.

The Protocol Suite version identifies a coherent release of the specification as a whole.

A change to one protocol does **not** necessarily require a new major version of the entire protocol suite.

---

# Protocol Suite Version

The Protocol Suite version identifies the revision of the AADAconnect Protocol Suite specification.

It represents the collection of protocol specifications released together.

The Protocol Suite version SHALL follow Semantic Versioning.

Example:

```text
AADAconnect Protocol Suite
Version 1.0.0
```

The Protocol Suite version is intended for documentation, specification releases, and reference purposes.

Individual implementations are expected to identify the versions of the specific protocols they support.

---

# Individual Protocol Version

Each protocol SHALL maintain an independent version.

Examples include:

| Protocol | Example Version |
|----------|-----------------|
| ADCP | 1.2.0 |
| APOP | 1.0.0 |
| AOTA | 1.1.0 |
| AADAcom | 0.4.0 |
| AADAnetSync | 0.2.0 |

A protocol MAY evolve independently without requiring changes to unrelated protocols.

---

# Semantic Versioning

All protocol versions SHALL use the format:

```text
MAJOR.MINOR.PATCH
```

## Major Version

The MAJOR version SHALL be incremented when introducing changes that intentionally break compatibility with previous versions.

Examples include:

- Removing required protocol fields.
- Changing mandatory message behavior.
- Introducing incompatible protocol semantics.

---

## Minor Version

The MINOR version SHALL be incremented when introducing new functionality while maintaining compatibility with previous minor versions of the same major version.

Examples include:

- New optional messages.
- Additional capabilities.
- New protocol extensions.

---

## Patch Version

The PATCH version SHALL be incremented when making corrections that do not affect protocol compatibility.

Examples include:

- Clarifications to the specification.
- Editorial improvements.
- Corrections to protocol definitions.
- Non-breaking implementation guidance.

Patch releases SHALL NOT introduce protocol-breaking changes.
---

# Version Lifecycle

Protocols evolve independently.

Implementations SHOULD support the protocol versions required by their intended deployment environment.

Deprecated behavior SHOULD remain documented until officially removed in a future major version.

Experimental protocols MAY use major version **0**, indicating that compatibility is not guaranteed between minor releases.

---

# Compatibility Principles

Protocol versions communicate implementation expectations rather than implementation age.

Implementations claiming support for a protocol SHALL implement the behavior defined by the supported protocol version.

Compatibility requirements between different protocol versions are defined in the Compatibility specification.

---

# Current Versioning Strategy

The current AADAconnect Protocol Suite follows these principles:

- Every protocol maintains an independent version.
- The Protocol Suite maintains its own version.
- Semantic Versioning is used throughout the specification.
- Experimental protocols may evolve more rapidly until stabilized.

As of this revision:

- ADCP is the most mature protocol but continue to evolve.
- APOP and AOTA are stable but continue to evolve.
- AADAcom and AADAnetSync remain under active development.

---

# Conformance

An implementation claiming compliance with the AADAconnect Protocol Suite SHALL follow the versioning rules defined in this document.

Protocol implementations SHALL accurately identify the protocol versions they support.

---

# Related Documents

## Normative References

- [Compatibility](Compatibility.md)

## Informative References

- [Architecture Overview](Overview.md)
- [Protocol Stack](ProtocolStack.md)

---

# Document Navigation

**Previous:** [Protocol Stack](ProtocolStack.md)

**Next:** [Compatibility](Compatibility.md)