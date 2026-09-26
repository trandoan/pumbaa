# 14. Assumptions

Assumption is first-class.

Example:

```text
Assumption:
FIS supports idempotent retry.
```

Lifecycle:

```text
ASSUMED
 ↓
VALIDATE
 ├── CONFIRMED
 └── INVALIDATED
```

Invalidated assumptions trigger Impact Analysis.

---
