# 39. Source Authority

There is no single universal source that is authoritative for every type of information.

Authority depends on the subject.

| Subject | Primary Authority |
|---|---|
| Current implementation | Git / current code |
| Business intent | Product / business evidence |
| UX / UI | Figma + UX decisions |
| What was said | Meeting evidence |
| Architecture decision | ADR / explicit decision evidence |
| Security standard | Enterprise security/platform standard |
| Test result | Test execution evidence |
| Production behavior | Production evidence |
| Work tracking | Rally |

When sources conflict:

```text
Source A
   +
Source B
   │
   ▼
Context Conflict
   │
   ▼
Question / Decision
   │
   ▼
Resolved Context
```

Do not silently choose one source.

---
