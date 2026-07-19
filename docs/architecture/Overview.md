# Architecture Overview

> Defines the architectural principles, scope, and organization of the AADAconnect Protocol Suite.

---

# Document Information

| Field | Value |
|-------|-------|
| Document | Architecture Overview |
| Category | Architecture |
| Document Type | Informative |
| Applies To | AADAconnect Protocol Suite |
| Status | Stable and Actively Developed |
| Version | 1.0 |
| Last Updated | 2026-07-19 |

---

# Purpose

This document provides a high-level overview of the AADAconnect Protocol Suite, its design philosophy, architectural principles, and the relationships between its constituent protocols.

It serves as the entry point for developers, implementers, and contributors seeking to understand the overall architecture before studying the individual protocol specifications.

This document is informative and does not define protocol behavior or implementation requirements.

---

# Scope

This document describes:

- The purpose of the AADAconnect Protocol Suite.
- The architectural goals of the protocol suite.
- The relationship between the protocols.
- The design philosophy that guides protocol development.

This document does **not** define:

- Protocol message formats.
- Packet structures.
- Transport-specific behavior.
- Authentication mechanisms.
- Device state machines.
- Timing requirements.

These topics are defined in the corresponding protocol specifications.

---

# Requirement Language

This document is informative.

Normative requirement keywords such as **MUST**, **SHALL**, and **SHOULD** are defined for the AADAconnect Protocol Suite but are generally not used within this document.

---

# Definitions

The following terms are used throughout the AADAconnect Protocol Suite.

| Term | Definition |
|------|------------|
| User Scope | The logical boundary containing the devices, applications, controllers, metadata, protocol state, credentials, and other participating entities belonging to a single AADAconnect deployment. |
| Protocol Entity | Any device, application, controller, service, or software component capable of participating in one or more AADAconnect protocols. |
| Device Authority | The architectural principle that devices remain the authoritative source of their own operational state whenever practical. |
| Fetch Payload | An authoritative protocol payload representing the current synchronized state of a specific category of platform information within a User Scope. |
| Fetch Snapshot | The current synchronized instance of a Fetch Payload available to participating entities. |
| Meta Payload | A protocol payload containing metadata referenced by one or more Fetch Payloads. |
| Snapshot Synchronization | The process by which protocol entities synchronize authoritative platform state through Fetch Payloads and Meta Payloads. |

---

# Table of Contents

1. Introduction
2. The AADAconnect Platform
3. The AADAconnect Protocol Suite
4. Design Goals
5. Architectural Principles
6. Current Protocols
7. Future Evolution
8. Related Documents

---

# Introduction

The AADAconnect Protocol Suite is a collection of communication protocols developed for the AADAconnect platform.

Rather than defining a single protocol for every task, the protocol suite separates responsibilities across multiple specialized protocols. Each protocol addresses a specific aspect of device communication, coordination, provisioning, or management while remaining interoperable with the rest of the suite.

This modular architecture allows protocols to evolve independently while maintaining a consistent overall design.

---

# The AADAconnect Platform

AADAconnect is an edge-native Internet of Things (IoT) platform designed to enable users to connect, provision, manage, monitor, analyze, and control their devices without requiring a cloud-dependent architecture.

The platform prioritizes user ownership of data and devices. Whenever practical, devices remain the authoritative source of operational state rather than relying on centralized cloud services.

Cloud services may be used where they provide practical benefits, such as remote connectivity or firmware distribution, but they are considered supporting infrastructure rather than the primary source of device state or control.

The objective is to provide the convenience commonly associated with cloud-based systems while preserving local ownership, operational independence, and long-term reliability.

---

# The AADAconnect Protocol Suite

The protocol suite provides standardized communication mechanisms for devices and software within the AADAconnect ecosystem.

Each protocol addresses a distinct responsibility.

Current protocols include:

| Protocol | Responsibility |
|----------|----------------|
| ADCP | Device coordination, remote management, monitoring, and control. |
| APOP | Device provisioning and onboarding. |
| AOTA | Firmware update management. |
| AADAcom | Embedded device-to-device communication. |
| AADAnetSync | Time and synchronization services for AADAcom. |

Protocols are designed to operate together while remaining independently versioned and specified.

---

# Design Goals

The AADAconnect Protocol Suite is designed with the following goals:

- Edge-native operation.
- Embedded-first architecture.
- Modular protocol design.
- Independent protocol evolution.
- User ownership of devices and data.
- Practical cloud interoperability without cloud dependence.
- Local operability whenever practical.
- Extensibility for future protocols and capabilities.
- Clear separation of protocol responsibilities.
- Consistent implementation across firmware and software components.

---

# Architectural Principles

The protocol suite is based on several core architectural principles.

## Separation of Responsibilities

Each protocol is responsible for a clearly defined domain.

Provisioning, coordination, firmware updates, and device-to-device communication are specified independently to reduce complexity and improve maintainability.

## Device Authority

Devices are the authoritative source of their operational state whenever practical.

Supporting services may cache or relay information but should not become the authoritative source of device state.

## Transport Independence

Protocols define communication behavior rather than being tightly coupled to a single transport technology wherever practical.

Specific transport mappings are documented within the respective protocol specifications.

## Independent Evolution

Protocols evolve independently through separate versioning while remaining part of a unified protocol suite.

## User-Scoped Architecture

AADAconnect follows a **user-scoped architecture**.

The platform is designed around independent **User Scopes** rather than a single global namespace.

A User Scope represents the logical boundary containing the devices, applications, controllers, metadata, protocol state, and other participating entities belonging to a single user or deployment.

All protocol operations are performed within a User Scope unless explicitly specified otherwise.

This architecture provides several advantages:

- Independent operation of multiple users.
- Isolation of protocol state.
- Simplified device coordination.
- Improved privacy.
- Reduced dependence on centralized cloud infrastructure.
- Natural edge-native operation.

Protocols within the AADAconnect Protocol Suite SHALL operate within a User Scope unless otherwise defined by their respective specifications.

The AADAconnect Platform MAY contain multiple independent User Scopes, but protocol state SHALL NOT be shared between User Scopes unless explicitly defined by a future specification.

---

# Current Protocols

The current protocol suite consists of:

- ADCP (AADA Device Coordination Protocol)
- APOP (AADA Provisioning Protocol)
- AOTA (AADA Over-the-Air Protocol)
- AADAcom
- AADAnetSync

Additional protocols may be introduced in future revisions of the specification.

---

# Future Evolution

The protocol suite is intended to evolve over time as new device categories, communication requirements, and deployment models emerge.

Future revisions may introduce additional protocols while preserving the overall architectural philosophy defined in this document.

---

# Related Documents

## Normative References

- [Versioning](Versioning.md)
- [Compatibility](Compatibility.md)
- [Security Model](SecurityModel.md)

## Informative References

- [Protocol Stack](ProtocolStack.md)

---

# Document Navigation

**Next:** [Protocol Stack](ProtocolStack.md)