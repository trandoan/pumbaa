# 17. Cross-Repository Impact

Repository is not the impact boundary.

Use an **Engineering Dependency Graph**.

Sources:

- Source code
- API specs
- Event schemas
- Imports/references
- Annotations
- Shared libraries
- Documentation
- Optional runtime evidence

Also maintain a **Contract Graph**.

Example:

```text
ArrangementUpdated v3
    ├── Consumer B
    ├── Consumer C
    └── Consumer D
```

Impact reports distinguish:

```text
POTENTIAL IMPACT
CONFIRMED IMPACT
```

Confidence means detection confidence, not quality score.

Blast Radius is scope, not ranking:

- Repositories
- Services
- Components
- APIs
- Events
- Tests
- Teams

Technical, design and business impact may differ.

---
