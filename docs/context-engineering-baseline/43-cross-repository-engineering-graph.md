# 43. Cross-Repository Engineering Graph

Repository is not the impact boundary.

The architecture therefore maintains an Engineering Dependency Graph.

Possible evidence sources:

- Source code
- Imports
- API specifications
- Event schemas
- Shared libraries
- Configuration
- Documentation
- Explicit architecture relationships
- Runtime evidence where available

The graph should distinguish:

```text
POTENTIAL IMPACT
```

from:

```text
CONFIRMED IMPACT
```

Detection confidence describes confidence in the **detection**, not a quality score.

Example:

```text
Service A
   │
   ├── calls API B
   │
   ├── consumes Event C
   │
   └── uses Library D
```

A change to B, C, or D can trigger impact analysis for A.

---
