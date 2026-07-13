# Protocol Stack

## Purpose

The AADAconnect Protocol Suite is composed of multiple protocols operating at different layers of the communication architecture. Each protocol is designed for a specific purpose while integrating with the others to provide a complete device ecosystem.

This document describes the relationship between the protocols and the transport technologies on which they operate.

---

# Overview

Unlike monolithic communication protocols, the AADAconnect Protocol Suite consists of independent protocols, each responsible for a well-defined area of functionality.

Some protocols build upon others, while some operate independently.

---

# Protocol Stack

```
                           AADAconnect Platform
┌────────────────────────────────────────────────────────────┐
│                    Dashboard / Applications                │
└────────────────────────────────────────────────────────────┘
                              │
                              │
                     AADAconnect Protocol Suite
                              │
        ┌─────────────────────┴─────────────────────┐
        │                                           │
        ▼                                           ▼
      ADCP                                      AADAcom
        │                                           │
   ┌────┴────┐                               AADAnetSync
   │         │
   ▼         ▼
 APOP      AOTA
        (Control & Coordination)
```

---

# Transport Stack

## ADCP

ADCP currently operates over MQTT.

```
Application
      │
      ▼
ADCP
      │
      ▼
MQTT
      │
      ▼
TCP
      │
      ▼
IP
      │
      ▼
Network
```

MQTT provides reliable message delivery between devices and management applications. The MQTT broker may be deployed locally or remotely depending on the deployment environment.

---

## APOP

APOP operates during device provisioning using a temporary wireless access point created by the device.

```
Dashboard
      │
      ▼
HTTP
      │
      ▼
JSON API
      │
      ▼
SoftAP
      │
      ▼
Device
```

Provisioning requests and responses are exchanged using HTTP with JSON payloads.

---

## AOTA

AOTA uses two communication paths.

### Control Path

Protocol coordination occurs through ADCP.

```
Dashboard
      │
      ▼
ADCP
      │
      ▼
MQTT
      │
      ▼
Device
```

Typical operations include:

- Update availability
- Version information
- Update initiation
- Progress reporting
- Completion notification
- Failure reporting

### Firmware Download Path

Firmware images are downloaded independently using HTTPS.

```
Device
      │
      ▼
HTTPS
      │
      ▼
Firmware Repository
(GitHub Releases or equivalent)
```

Separating firmware transfer from protocol coordination reduces load on the messaging infrastructure while allowing standard HTTPS infrastructure to distribute firmware images efficiently.

---

## AADAcom

AADAcom is an embedded communication protocol designed for direct device-to-device communication.

```
Application
      │
      ▼
AADAcom
      │
      ▼
IEEE 802.11 MAC / Wi-Fi
      │
      ▼
Peer Device
```

Unlike ADCP, AADAcom does not depend on MQTT for communication and is intended for low-latency embedded networking.

---

## AADAnetSync

AADAnetSync operates as a synchronization layer within AADAcom.

```
Application
      │
      ▼
AADAnetSync
      │
      ▼
AADAcom
      │
      ▼
IEEE 802.11 MAC / Wi-Fi
```

It provides synchronization services required by distributed applications such as multi-device audio playback.

---

# Design Considerations

The protocol stack is designed with the following objectives:

- Independent protocol evolution
- Clear separation of responsibilities
- Efficient operation on embedded systems
- Minimal protocol coupling
- Reuse of established transport technologies where appropriate
- Native communication when application requirements demand lower latency

---

# Protocol Independence

Each protocol defines its own behavior and versioning.

A device is not required to implement every protocol within the AADAconnect Protocol Suite.

For example:

- A Smart Plug may implement ADCP, APOP and AOTA.
- A Smart Speaker may additionally implement AADAcom and AADAnetSync.

This modular approach allows different device classes to implement only the protocols necessary for their intended functionality.

---

# Related Documents

- Overview.md
- NamingConvention.md
- Versioning.md
- Compatibility.md
- SecurityModel.md