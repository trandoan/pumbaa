# 3. Three Entry Points

## 3.1 Business / Product Change

```text
Business Outcome
    ↓
Requirement Seed
    ↓
Requirement Discovery
    ↓
Context Assessment
    ↓
Requirement Baseline
```

## 3.2 Engineering Change

For:

- Security patch
- Platform upgrade
- Infrastructure change
- Dependency/library upgrade
- External system change
- Architecture change
- Enterprise standard/policy change

```text
Platform / Security / Infra / Dependency / External System
    ↓
Engineering Change
    ↓
Impact Analysis
    ↓
Design / Implementation / Test / Release as required
```

Engineering Change is **not automatically a business requirement**.

## 3.3 Production / Engineering Feedback

Triggers:

- Defect
- Incident
- Monitoring signal
- Production observation
- Developer discovery
- Performance observation
- Operational feedback
- User feedback

```text
Feedback
    ↓
Defect / Incident / Change
    ↓
Impact Analysis
    ↓
Context / Design / Code / Test / Operations updates as required
```

All three entry points converge on **Impact Analysis**.

---
