```mermaid
stateDiagram-v2
    NORMAL --> WARNING : envelope approaching
    WARNING --> DEGRADED : limit exceeded
    DEGRADED --> CRITICAL : safety margin exhausted
    WARNING --> NORMAL : recovered
```

