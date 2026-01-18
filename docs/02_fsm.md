---
title: "envelope-control"
description: "control architectures that explicitly treat operational envelopes"
---

# Finite State Machine (FSM)

## Purpose

The FSM governs **what control actions are permitted** based on envelope status.

It does not:
- optimize performance,
- tune gains,
- estimate states.

---

## States

```
NORMAL
WARNING
DEGRADED
CRITICAL
```

---

## State Semantics

### NORMAL
- Full control authority
- Nominal objectives allowed

### WARNING
- Control authority constrained
- Conservative limits enforced

### DEGRADED
- Fixed degraded mode
- Only predefined safe actions allowed

### CRITICAL
- Recovery or shutdown only
- No adaptive behavior permitted

---

## Transitions

Transitions are triggered solely by:
- envelope threshold crossings
- persistence timers

No transition is triggered by performance metrics.

---

## FSM Responsibilities

- Permit or deny control actions
- Freeze unsafe reconfiguration
- Enforce operational priorities

---

## FSM Non-Responsibilities

- Gain computation
- Model adaptation
- Decision optimization

---
*FSM exists to say “no” clearly and immediately.*

