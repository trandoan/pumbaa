# 19. Platform / Security / Infrastructure Changes

These are not automatically Scrum features.

```text
Platform/Security Notice
    ↓
Engineering Change
    ↓
Impact Analysis
    ↓
Affected repositories/services
    ↓
Compatibility Analysis
    ↓
Implementation / Design / Test if required
    ↓
Production Readiness
```

Three common levels:

### Level 1 — Implementation-only

Patched dependency, behavior/contract stable.

### Level 2 — Compatibility/design impact

Examples:

- Framework API changes
- Serialization behavior
- Transaction behavior
- Security configuration
- Connection pool
- Kafka client

### Level 3 — Architecture impact

Existing mechanism no longer supported and must be replaced.

Then HLD/component design may need changes.

Enterprise standards can be modeled as inherited constraints.

Example:

```text
STD-SEC-021
Approved library >= X
```

Standard change:

```text
Standard Change
    ↓
Impact Analysis
    ↓
Affected Services
```

---
