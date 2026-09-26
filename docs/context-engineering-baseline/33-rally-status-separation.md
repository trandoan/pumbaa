# 33. Rally Status Separation

Do not overload one status field.

Separate at least:

### Delivery Status

```text
DEFINED
IN_PROGRESS
DONE
```

### Context Status

```text
CURRENT
SUPERSEDED
UNDER_REVIEW
IMPACTED
ARCHIVED
```

### Change / Impact Status

```text
DETECTED
ANALYZING
CONFIRMED
REWORK_REQUIRED
IN_PROGRESS
RESOLVED
NOT_AFFECTED
```

Other independent statuses may include:

- Requirement Status
- Decision Status
- Production Readiness Status
- Release Status
- Operational Status
- Evidence Status

Example:

```text
US-145

Delivery Status:
DONE

Context Status:
IMPACTED

Change Impact:
REWORK_REQUIRED
```

The Rally card remains DONE.

---
