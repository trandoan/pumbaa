# 21. Operational Context

Operational Context describes what must be known and acted upon in production.

```text
Operational Context
├── Health
├── Traffic
├── Latency
├── Error
├── Dependency
├── Business Metrics
├── Infrastructure
├── Metric
├── Monitoring
├── Alert
├── Dashboard
├── Runbook
└── Ownership
```

Monitoring should not be limited to infrastructure metrics.

## Technical Metrics

- Request count
- Latency
- Error rate
- DB latency
- Dependency failures

## Business Metrics

- Transaction success
- Transaction failure
- Rejected transaction

## Integration Metrics

- Event publish failure
- Consumer lag
- Processing failure
- Duplicates
- DLQ

Business rules can generate candidate business metrics.

---
