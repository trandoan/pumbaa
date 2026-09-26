# 34. DONE Rally Items Must Never Be Reopened

Company process requires that a DONE Rally card must not be reopened.

Therefore:

```text
DONE Work Item
      │
      ▼
New Change Detected
      │
      ▼
Impact Analysis
      │
      ▼
Required Action
      │
      ▼
New Rally Work Item
```

Never:

```text
DONE
 ↓
REOPEN
```

Instead:

```text
Original Work Item
        │
        └── remains DONE

New Context Change
        │
        ▼
New Required Action
        │
        ▼
New Rally Work Item
```

This preserves both delivery history and engineering history.

---
