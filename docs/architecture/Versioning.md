# Versioning

## Purpose

This document defines the versioning policy for the AADAconnect Protocol Suite and its individual protocols.

A consistent versioning policy allows protocol implementations to evolve in a predictable manner while maintaining interoperability between compatible implementations.

Unless otherwise specified, all protocols within the AADAconnect Protocol Suite SHALL follow the rules defined in this document.

---

# Overview

The AADAconnect Protocol Suite consists of multiple independent protocols.

Each protocol evolves independently and therefore maintains its own protocol version.

In addition to individual protocol versions, the AADAconnect Protocol Suite itself maintains a separate version representing the overall specification release.

Example:

| Component | Version |
|-----------|----------|
| AADAconnect Protocol Suite | 1.0.0 |
| ADCP | 1.2.0 |
| APOP | 1.0.0 |
| AOTA | 0.8.0 |
| AADAcom | 0.4.0 |
| AADAnetSync | 0.2.0 |

---

# Version Format

All versions SHALL follow Semantic Versioning (SemVer).

```
MAJOR.MINOR.PATCH
```

Example:

```
1.0.0
1.4.2
2.0.0
```

---

# Version Components

## Major Version

A major version SHALL be incremented when protocol changes are not backward compatible.

Typical examples include:

- Removal of protocol messages.
- Incompatible packet formats.
- Changes to required protocol behavior.
- Breaking interoperability with previous implementations.

Example:

```
ADCP 1.x.x
↓

ADCP 2.0.0
```

An implementation supporting ADCP 1.x is not expected to communicate correctly with ADCP 2.x unless compatibility mechanisms are explicitly defined.

---

## Minor Version

A minor version SHALL be incremented when new functionality is introduced without breaking existing implementations.

Typical examples include:

- New message types.
- Additional optional fields.
- New protocol capabilities.
- Additional commands.

Implementations supporting an earlier minor version SHOULD continue to interoperate with newer implementations whenever practical.

Example:

```
1.2.0
↓

1.3.0
```

---

## Patch Version

A patch version SHALL be incremented for changes that do not modify protocol interoperability.

Examples include:

- Specification clarifications.
- Editorial corrections.
- Documentation improvements.
- Non-breaking implementation guidance.

Patch releases SHALL NOT introduce protocol-breaking changes.

---

# Independent Protocol Versioning

Each protocol within the AADAconnect Protocol Suite SHALL maintain its own version.

Updating one protocol does not require updating every other protocol.

Example:

```
ADCP        1.4.0
APOP        1.1.0
AOTA        0.9.0
AADAcom     0.5.0
```

This allows protocols to evolve independently while minimizing unnecessary specification updates.

---

# Protocol Suite Version

The AADAconnect Protocol Suite SHALL also maintain its own version.

The protocol suite version represents the published specification as a whole and does not imply that every protocol has changed.

A new suite version MAY include:

- New protocol releases.
- New specifications.
- Updated architecture documents.
- Documentation improvements.

---

# Experimental Protocols

Protocols under active development SHOULD use a major version of zero.

Example:

```
0.1.0
0.2.0
0.5.0
```

Experimental protocols are subject to incompatible changes before reaching version 1.0.0.

Example:

- AADAcom
- AADAnetSync
- Early AOTA revisions

---

# Compatibility

Each protocol specification SHALL explicitly state its compatibility expectations.

Compatibility information SHOULD identify:

- Supported protocol versions.
- Incompatible protocol versions.
- Deprecated features.
- Migration guidance where applicable.

Example:

```
Compatible with

ADCP 1.x

Not Compatible with

ADCP 2.x
```

The reason for incompatibility SHOULD be documented whenever compatibility is intentionally broken.

---

# Deprecation Policy

Protocol features are not required to be removed immediately when superseded.

Depending on the nature of the change, a feature MAY:

- Remain fully supported.
- Be marked as deprecated.
- Be removed in a future major version.
- Be removed immediately if required for security, correctness, or protocol integrity.

Each protocol specification SHALL clearly identify deprecated behavior and any planned removal schedule.

---

# Document Version Information

Protocol specification documents SHOULD include version information where appropriate.

Example:

| Field | Value |
|-------|-------|
| Protocol | ADCP |
| Protocol Version | 1.2.0 |
| Specification Version | 1.0 |
| Status | Stable |
| Last Updated | YYYY-MM-DD |

This metadata assists implementers in identifying the applicable specification.

---

# Version History

Each protocol SHALL maintain an independent version history documenting protocol evolution.

Version history SHOULD include:

- Version number.
- Release date.
- Summary of changes.
- Compatibility impact.

Detailed version histories are maintained within the corresponding protocol documentation.

---

# Related Documents

- Overview.md
- ProtocolStack.md
- Compatibility.md
- SecurityModel.md