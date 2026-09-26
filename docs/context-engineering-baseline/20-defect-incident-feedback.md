# 20. Defect / Incident / Feedback

A defect is a divergence between expected and actual behavior.

Defect types:

```text
REQUIREMENT_DEFECT
DESIGN_DEFECT
IMPLEMENTATION_DEFECT
TEST_DEFECT
INTEGRATION_DEFECT
DATA_DEFECT
ENVIRONMENT_DEFECT
```

Capture:

- Environment
- Version/commit
- Scenario
- Input
- Expected
- Actual
- Logs/evidence
- Timestamp
- Requirement
- Design
- Code
- Test
- Change

Use:

```text
Expected
   ↓
Requirement
   ↓
Acceptance Criteria
   ↓
UX
   ↓
HLD
   ↓
Component
   ↓
Implementation
   ↓
Test
   ↓
Reality
```

Then identify where divergence happened.

Before broad changes:

```text
SUSPECTED_IMPACT
```

AI identifies potential impact.

Humans confirm.

---
