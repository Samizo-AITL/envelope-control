---
title: "envelope-control"
description: "control architectures that explicitly treat operational envelopes"
---

# Operational Envelope Definition

## Overview

An **operational envelope** defines the admissible region of operation
for sensors, actuators, and power subsystems.

Each envelope is defined with **two thresholds**:
- **Warning**: approaching limits
- **Limit**: exceeded safe operation

---

## Sensor Envelope

| Condition | Description |
|---------|-------------|
| Valid | Sensor within nominal accuracy |
| Degraded | Bias, noise, or delay exceeds warning threshold |
| Invalid | Stuck, saturated, or inconsistent |

Sensor envelopes determine **whether a sensor may be used**.

---

## Actuator Envelope

| Condition | Description |
|----------|-------------|
| Nominal | Commanded effort achievable |
| Saturating | Persistent saturation detected |
| Limited | Reduced authority available |

Actuator envelopes determine **maximum admissible control effort**.

---

## Power Envelope (V–I)

| Quantity | Warning | Limit |
|--------|---------|-------|
| Voltage (V) | Near minimum | Below minimum |
| Current (I) | Sustained high | Overcurrent |
| Power (P=V·I) | Reduced margin | Exceeded |

Power envelope violations override all performance objectives.

---

## Envelope States

Envelope status is classified as:

- **NORMAL** – all envelopes valid
- **WARNING** – approaching limits
- **DEGRADED** – limits exceeded, operation restricted
- **CRITICAL** – continued operation unsafe

---

## Design Rule

Envelope boundaries are:
- predefined,
- conservative,
- immutable during runtime.

---
*An envelope defines what the system is allowed to attempt.*

