# 28. Security Evidence

Security evidence must be traceable to the exact implementation being released.

Minimum useful information:

```text
SecurityEvidence
├── repository
├── commit
├── build/version
├── scan_timestamp
├── security_tool
├── result
├── vulnerabilities
├── exceptions
└── release/change
```

For example:

```text
Repo: payment-service
Commit: abc123
Version: 2.8.1
Tool: Snyk
Scan: 2026-09-26
Result: ...
```

A security result is not timeless.

If implementation changes:

```text
Code Change
     │
     ▼
Previous Security Evidence
     │
     ▼
Potentially Stale
     │
     ▼
Rescan Required
```

Therefore security evidence should have temporal validity.

---
