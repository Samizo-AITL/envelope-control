---
title: Role of LLM
---

# Role of LLM in Envelope Control

## Allowed Role

An LLM may be used to:

- propose reconfiguration plans
- suggest estimator or allocator changes
- summarize system degradation
- generate design-time artifacts

---

## Prohibited Role

An LLM must NOT:

- issue real-time control commands
- modify envelope definitions
- trigger FSM transitions
- bypass safety constraints

---

## Interaction Model

1. FSM determines current envelope state
2. Allowed actions are enumerated
3. LLM generates proposals within constraints
4. Mechanical guards validate proposals
5. Accepted changes are applied incrementally

---

## Design Principle

LLM outputs are **advisory, not authoritative**.

---
*The LLM may speak, but it may not act.*

