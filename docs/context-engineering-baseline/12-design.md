# 12. Design

Three parallel design branches:

```text
Requirement
    │
    ├── Experience Design
    ├── Solution Design
    └── Operational Design
```

---

## 12.1 Experience Design

Possible entities:

- UX Requirement
- UX Flow
- UI Screen
- UI Component
- UI State
- Interaction
- Design Decision
- Design Asset

Figma provides UX/UI context.

UI changes may impact backend/API/tests, but impact must be determined.

---

## 12.2 Solution Design

Includes:

- HLD
- Architecture decisions
- Component design
- API design
- Event design
- Data/schema design
- Dependency relationships

HLD answers:

> Where does what interact?

Component Design answers:

> How is responsibility decomposed?

Implementation Context answers:

> What does the code need to do?

Traceability:

```text
Business Outcome
    ↓
Requirement
    ↓
HLD Decision
    ↓
Component Constraint
    ↓
Code
```

If code diverges from design, flag the divergence.

Humans decide whether code or design should change.

---

## 12.3 Operational Design

Operational Design is first-class.

It covers:

- Monitoring
- Alerting
- Dashboards
- Runbooks
- Support model
- Ownership
- Escalation
- Failure modes
- Operational verification

Operational context starts during design, not at Go-Live.

---
