# 4. Context Graph

The Context Graph is the central relationship and semantic layer.

It connects:

```text
Business Outcome
Capability
Requirement
Business Rule
NFR
Question
Decision
Assumption

UX Requirement
UX Flow
Design
HLD
Component Design
API Contract
Event Contract
Data / Schema

Implementation Intent
Repository
Service
Code
Dependency

Test Intent
Test Scenario
Test Execution
Test Evidence
Security Evidence
Operational Evidence

Defect
Incident
Feedback
Change
Impact
Required Action

Operational Context
Metric
Monitoring
Alert
Dashboard
Runbook
Ownership
Escalation

Release
Production Readiness
Compliance Requirement
Approval
Deployment
Post-Go-Live Validation

Work Item
Rally Reference

Raw Evidence
Checkpoint
Conflict
```

### Key principle

> **Catalog is a map, not a cache.**

Do not maintain a brittle exact-file inventory as the primary source of truth.

Current source is discovered dynamically from Git/repository state.

Local code-analysis cache may be keyed by Git commit.

---
