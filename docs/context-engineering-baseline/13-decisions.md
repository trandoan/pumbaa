# 13. Decisions

Decision is a first-class entity.

Example:

```yaml
id: D-201
type: architecture_decision
statement: Use Kafka for asynchronous event propagation
applies_to:
  - Service-A
affects:
  - Event Contract X
  - Consumer B
source:
  - ADR-201
status: DECIDED
```

Lifecycle:

```text
PROPOSED
 ↓
DISCUSSED
 ↓
DECIDED
 ↓
IMPLEMENTED
 ↓
VALIDATED
 ↓
SUPERSEDED
```

Decisions link to evidence.

Do not delete superseded decisions.

---
