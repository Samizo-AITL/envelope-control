---
title: "envelope-control"
description: "control architectures that explicitly treat operational envelopes"
---

# 🧠 Role of LLM in Envelope Control

## ✅ Allowed Role

A Large Language Model (LLM) **may be used strictly as an advisory component**.

Permitted uses include:

- 🛠 proposing reconfiguration or recovery plans  
- 📐 suggesting estimator, allocator, or controller structure changes  
- 📉 summarizing observed system degradation or envelope violations  
- 📝 generating **design-time or offline artifacts** (documents, code drafts, reports)

At no point does the LLM hold operational authority.

---

## 🚫 Prohibited Role

An LLM must **never**:

- 🎮 issue real-time control commands  
- 📦 modify operational envelope definitions  
- 🔄 trigger FSM state transitions  
- 🧱 bypass or weaken safety and envelope constraints  

Any attempt to cross these boundaries must be **explicitly rejected**.

---

## 🔗 Interaction Model

The interaction between the control system and the LLM follows a **strictly gated pipeline**:

1. 🧭 **FSM determines the current envelope state**  
2. 📋 **Allowed actions are explicitly enumerated**  
3. 🧠 **LLM generates proposals within those constraints**  
4. 🛡 **Mechanical guards validate proposals**  
5. 🔁 **Accepted changes are applied incrementally and reversibly**

The LLM never operates outside the permissions defined by the FSM and envelope states.

---

## 📜 Design Principles

| Principle | Meaning |
|---------|---------|
| 🔐 **Advisory Only** | LLM outputs inform, but do not decide |
| 🧱 **Hard Gating** | All proposals pass deterministic guards |
| 🧭 **Envelope Supremacy** | FSM and envelopes always dominate |
| 🕰 **No Real-Time Authority** | LLM is excluded from fast control loops |

---

> 💡 *An LLM can reason, explain, and suggest.*  
>  
> **But it must never decide or execute.**  
>  
> *The LLM may speak, but it may not act.*
