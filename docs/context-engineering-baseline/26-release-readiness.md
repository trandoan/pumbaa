# 26. Release Readiness

Release Readiness là một **cross-cutting readiness package**, không phải một bước chỉ xuất hiện ngay trước go-live.

```text
Change
  │
  ├── Security / Compliance
  ├── Testing / Quality
  ├── Documentation / Paperwork
  ├── Deployment / Rollback
  └── Operations
          │
          ▼
  Production Readiness
          │
          ▼
        Release
```

## 26.1 Release Readiness Package

Release readiness có thể bao gồm:

### Change

- Change description
- Reason for change
- Affected services/repositories
- Business outcome / requirement
- Change impact
- Design impact
- Dependency impact
- Cross-repo impact

### Security / Compliance

- Snyk scan
- Dependency compliance
- Vulnerability status
- Security exceptions
- Security approvals
- Required paperwork
- Compliance evidence

### Quality

- Unit test evidence
- Component test evidence
- Integration test evidence
- SIT evidence
- UAT evidence
- Regression evidence
- Performance evidence
- Security test evidence
- Operational verification evidence

### Documentation

- Implementation plan
- Deployment plan
- Rollback plan
- Release form
- Runsheet
- Architecture/design references
- Configuration changes
- Dependency changes

### Governance

- Architecture review
- Security review
- Required approvals
- Exception approvals

### Operations

- Dashboard
- Monitoring
- Alerting
- Runbook
- Ownership
- Escalation
- Support model

Not every release requires every artifact.

Applicability must be determined from context.

---
