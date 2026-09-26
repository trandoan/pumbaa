# 47. Temporal Model

Context evolves over time.

Do not overwrite history.

Recommended validity states:

```text
CURRENT
SUPERSEDED
UNDER_REVIEW
HISTORICAL
ARCHIVED
```

Example:

```text
Decision D1
   │
   ▼
Superseded by D2
```

D1 remains available for historical traceability.

The system should be able to answer:

> "What did we believe/decide at that point in time?"

as well as:

> "What is true now?"

---
