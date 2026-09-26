# 7. Requirement Discovery

High-level PO input becomes a **Requirement Seed**.

Example:

```yaml
id: R-SEED-001
intent: Customer can modify arrangement after creation
source: PO
status: DISCOVERY
```

Flow:

```text
Requirement Seed
    ↓
Requirement Discovery
    ↓
Requirement Gap Map
    ↓
Question Backlog
    ↓
Answers / Decisions / Evidence
    ↓
Requirement Baseline
```

AI must **not invent missing requirements**.

AI should identify:

- Ambiguity
- Missing information
- Conflicts
- NFR gaps
- Dependencies
- Unanswered questions

---
