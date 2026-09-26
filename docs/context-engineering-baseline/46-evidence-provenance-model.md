# 46. Evidence / Provenance Model

Every important context item should be traceable to evidence where possible.

Conceptually:

```text
Context Entity
     │
     ├── source
     ├── source_type
     ├── source_reference
     ├── timestamp
     ├── validity
     ├── confidence
     └── derived_from
```

Evidence can be:

- Direct
- Derived
- Inferred

The distinction must remain explicit.

Example:

```text
Meeting:
"Maybe use Kafka."

≠

Decision:
"We will use Kafka."

≠

Implementation Evidence:
"Service publishes events to Kafka."
```

These are three different facts with different evidentiary strength.

---
