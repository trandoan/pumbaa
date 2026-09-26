# 38. Context Views

The Context Graph should produce phase-specific views rather than forcing users to consume the entire graph.

## 38.1 Developer View

```text
Developer View
├── Business Outcome
├── Requirement
├── Acceptance Criteria
├── Design
├── Component
├── Constraints
├── Implementation Intent
├── Dependencies
├── Tests
├── Open Questions
└── Operational Expectations
```

Purpose:

> Give the developer enough context to implement correctly without reading the entire knowledge base.

---

## 38.2 Reviewer View

```text
Reviewer View
├── Why
├── What
├── Affected Context
├── Decisions
├── Risks
├── Dependencies
├── Evidence
├── Tests
└── Impact
```

The reviewer should be able to understand:

- Why this change exists
- What changed
- Which contexts are affected
- Which decisions support the change
- What risks exist
- What evidence exists
- What was tested
- Whether cross-repo effects exist

---

## 38.3 Release View

```text
Release View
├── Change
├── Affected Services
├── Readiness
├── Compliance
├── Testing Evidence
├── Paperwork
├── Approvals
├── Deployment
├── Rollback
└── Monitoring
```

---

## 38.4 Operations View

```text
Operations View
├── Service
├── Dependencies
├── Dashboard
├── Alerts
├── Thresholds
├── Runbook
├── Ownership
├── Escalation
└── Expected Behavior
```

---

## 38.5 Resume View

```text
Resume View
├── Last Checkpoint
├── Current State
├── Changes Since Checkpoint
├── Open Questions
├── Active Risks
└── Pending Decisions
```

This is the primary view for long-running work.

---
