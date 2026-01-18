---
title: "envelope-control"
description: "control architectures that explicitly treat operational envelopes"
---

# 🔄 Finite State Machine (FSM)

## 🎯 Purpose

The **Finite State Machine (FSM)** governs  
**what control actions are permitted** based on the current **envelope status**.

The FSM is intentionally **not a controller**.

It does **not**:
- 📈 optimize performance,
- 🎚 tune gains,
- 🧮 estimate system states.

Its sole role is **permission and refusal**.

---

## 🧩 Envelope-Driven States

The FSM operates on a small, explicit set of envelope-driven states:
```
NORMAL → WARNING → DEGRADED → CRITICAL
```


These states reflect **operational admissibility**,  
not internal plant dynamics.

---

## 📖 State Semantics

### 🟢 NORMAL
- Full control authority granted
- Nominal performance objectives allowed
- All certified control modes permitted

---

### 🟡 WARNING
- Control authority **constrained**
- Conservative limits enforced
- High-risk modes disabled

---

### 🟠 DEGRADED
- Fixed, predefined degraded mode
- Only explicitly approved safe actions allowed
- No reconfiguration or adaptation permitted

---

### 🔴 CRITICAL
- Recovery, fail-safe, or shutdown only
- All non-essential actions denied
- **No adaptive or exploratory behavior permitted**

---

## 🔁 State Transitions

FSM transitions are triggered **only** by:

- 📦 envelope threshold crossings  
- ⏱ persistence or debounce timers  

🚫 Transitions are **never** triggered by:

- tracking error,
- cost functions,
- performance metrics.

This guarantees **predictable and certifiable behavior**.

---

## 🛡 FSM Responsibilities

The FSM is responsible for:

- ✅ permitting or denying control actions  
- ❄ freezing unsafe reconfiguration attempts  
- 🧭 enforcing operational priorities  

It defines *what is allowed*, not *how it is achieved*.

---

## 🚫 FSM Non-Responsibilities

The FSM explicitly does **not** handle:

- 🎚 gain computation  
- 🔁 model adaptation  
- 📊 decision optimization  

These belong to lower or outer layers, if present.

---

> 💡 *The FSM does not decide how to act.*  
>  
> **It exists to say “no” clearly, deterministically, and immediately.**
