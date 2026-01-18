---
title: "envelope-control"
description: "control architectures that explicitly treat operational envelopes"
---

# 📐 Operational Envelope Definition

## 🧭 Overview

An **operational envelope** defines the **admissible region of operation**  
for the following subsystems:

- 📡 Sensors  
- 🦾 Actuators  
- ⚡ Power subsystems (V–I–P)

Each envelope is defined using **two explicit thresholds**:

| Threshold | Meaning |
|---------|---------|
| ⚠ **Warning** | Approaching operational limits |
| 🚫 **Limit** | Safe operation exceeded |

🚨 Crossing a limit is treated as a **control-relevant event**,  
not as a minor disturbance or noise artifact.

---

## 📡 Sensor Envelope

| Condition | Description |
|---------|-------------|
| ✅ **Valid** | Sensor within nominal accuracy and latency |
| ⚠ **Degraded** | Bias, noise, or delay exceeds warning threshold |
| 🚫 **Invalid** | Stuck, saturated, inconsistent, or implausible |

🔍 Sensor envelopes determine:

> **Whether a sensor is permitted to participate in control decisions**

Invalid sensors must be explicitly excluded from control loops.

---

## 🦾 Actuator Envelope

| Condition | Description |
|----------|-------------|
| ✅ **Nominal** | Commanded effort is fully achievable |
| ⚠ **Saturating** | Persistent saturation or rate limiting detected |
| 🚫 **Limited** | Reduced authority or partial availability |

🎚 Actuator envelopes determine:

> **The maximum admissible control effort**

Commands beyond the envelope are explicitly refused or reshaped.

---

## ⚡ Power Envelope (V–I)

| Quantity | ⚠ Warning | 🚫 Limit |
|--------|-----------|----------|
| **Voltage (V)** | Near minimum operating voltage | Below minimum voltage |
| **Current (I)** | Sustained high current | Overcurrent detected |
| **Power (P = V·I)** | Reduced power margin | Power limit exceeded |

🔋 Power envelope violations:

- override all performance objectives,
- may restrict or disable subsystems,
- take precedence over sensor and actuator envelopes.

---

## 🧩 Envelope States

Overall envelope status is classified into discrete system states:

| State | Meaning |
|------|---------|
| 🟢 **NORMAL** | All envelopes within nominal region |
| 🟡 **WARNING** | One or more envelopes near limits |
| 🟠 **DEGRADED** | Limits exceeded; operation restricted |
| 🔴 **CRITICAL** | Continued operation is unsafe |

These states are intended to drive **FSM mode transitions**.

---

## 📜 Design Rules

Operational envelope boundaries are:

- 🧱 **Predefined** at design time  
- 🛡 **Conservative** to ensure margin  
- 🔒 **Immutable during runtime**  

Dynamic or learned redefinition of envelopes is explicitly excluded.

---

> 💡 *An operational envelope does not define what the system should do.*  
>  
> **It defines what the system is allowed to attempt.**
