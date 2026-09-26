# 16. Testing / Verification

Testing is cross-cutting.

```text
What must we prove?
        ↓
Test Intent
        ↓
Test Scenario
        ↓
Implementation / Test
        ↓
Verification
        ↓
Evidence
```

Example:

```text
Test Intent:
Arrangement update must be idempotent.

Scenario:
Submit same request twice.

Implementation:
ArrangementServiceTest.java
```

Async Kafka designs may require testing:

- Publish
- Schema compatibility
- Duplicate events
- Ordering
- Consumer failure
- Retry
- DLQ
- Idempotency
- Eventual consistency

Verification can include:

- Unit
- Component
- Integration
- SIT
- UAT
- Regression
- Performance
- Security
- Operational verification

Important:

> Release cares about evidence, not just a status saying "passed."

---
