# 18. Change

Change is a first-class entity.

Possible triggers:

```text
BUSINESS_CHANGE
REQUIREMENT_CHANGE
DESIGN_CHANGE
DEFECT
INCIDENT
SECURITY
PLATFORM_UPGRADE
INFRA_CHANGE
DEPENDENCY_UPGRADE
EXTERNAL_SYSTEM_CHANGE
```

Change contains:

- Trigger
- Source
- Reason
- Affected context
- Impact
- Required actions
- Results
- Evidence

Generic flow:

```text
Change
   ↓
Impact Analysis
   ↓
Affected Context
   ↓
Required Actions
   ↓
Work / Design / Code / Test / Release / Operations
```

---
