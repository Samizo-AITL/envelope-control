---
title: V–I Envelope Example
---

# V–I Envelope Example

A system experiences battery degradation during operation.

- Voltage drops below warning threshold
- Maximum current remains available

Result:
- FSM enters WARNING
- Maximum thrust limited
- Aggressive maneuvers prohibited

If voltage drops further:
- FSM enters DEGRADED
- Fixed safe mode enforced

No optimization is attempted beyond envelope limits.

