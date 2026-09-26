# 30. Production Feedback

Production feedback is a first-class source of engineering context.

Possible sources:

- Monitoring
- Alert
- Incident
- User feedback
- Business feedback
- Performance observation
- Support feedback
- Developer discovery
- Production logs
- Production metrics

Not every production signal is a defect.

Possible classification:

```text
Production Feedback
├── Incident
├── Defect
├── Monitoring Signal
├── Performance Observation
├── User Feedback
├── Operational Feedback
└── Developer Discovery
```

Each may result in:

```text
Feedback
   │
   ▼
Impact Analysis
   │
   ├── Context change
   ├── Requirement change
   ├── Design change
   ├── Code change
   ├── Test change
   └── Operational change
```

---
