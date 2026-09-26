# 22. Alerting

Alert relationships:

```text
Alert
 ↓
Metric
 ↓
Operational Requirement / NFR / Business Rule
 ↓
Runbook
 ↓
Owner
 ↓
Escalation
```

Example:

```text
Alert:
Arrangement update failure rate > 5% for 5 minutes

Possible causes:
- FIS unavailable
- DB failure
- Kafka failure
- Validation issue

Runbook:
- check FIS connectivity
- inspect errors
- check dependency latency
- check Kafka lag
```

AI must not invent thresholds where no authoritative source exists.

---
