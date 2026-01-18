---
title: "envelope-control"
description: "control architectures that explicitly treat operational envelopes"
---

# 🔋 V–I Envelope Example

## 🧭 Scenario Overview

A system experiences **battery degradation during operation**.

The degradation primarily affects **voltage (V)**,  
while **current capability (I)** initially remains available.

This example illustrates how **Envelope Control reacts without optimization**.

---

## ⚡ Initial Condition

| Quantity | Status |
|--------|--------|
| 🔋 Voltage (V) | Within nominal range |
| ⚡ Current (I) | Fully available |
| 🧠 FSM State | 🟢 NORMAL |

All control modes are permitted.

---

## ⚠ Voltage Warning Threshold Crossed

As battery degradation progresses:

- 🔋 Voltage drops **below the warning threshold**
- ⚡ Maximum current **remains available**

### Resulting System Behavior

| Aspect | Effect |
|------|--------|
| 🧠 FSM State | 🟡 WARNING |
| 🦾 Control Authority | Constrained |
| 🚀 Thrust | Limited |
| 🔄 Maneuvers | Aggressive actions prohibited |

The system does **not** attempt to compensate by:
- increasing duty cycles,
- demanding higher currents,
- or relaxing envelope constraints.

---

## 🚫 Voltage Limit Exceeded

If voltage continues to decline:

- 🔋 Voltage drops **below the limit threshold**

### Resulting System Behavior

| Aspect | Effect |
|------|--------|
| 🧠 FSM State | 🟠 DEGRADED |
| 🎚 Control Mode | Fixed safe mode |
| 🔁 Adaptation | Disabled |
| 🛡 Priority | System survival |

Only predefined, certified behaviors are allowed.

---

## 🛑 Key Observation

No optimization or recovery attempt is performed  
**beyond the defined V–I envelope**.

The system accepts reduced capability  
instead of risking irreversible damage.

---

> 💡 *Envelope Control does not ask:*  
> “How can we still achieve performance?”  
>  
> **It asks:**  
> “What is the safest action that remains admissible now?”  
