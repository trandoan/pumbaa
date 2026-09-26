# 1. Problem

Enterprise software delivery often loses context between:

- Product/PO requirements
- Confluence documentation
- Figma designs
- meetings
- architecture decisions
- implementation
- tests
- cross-repository dependencies
- security/platform changes
- release paperwork
- monitoring/alerting
- production incidents

Typical symptoms:

- Developers receive high-level requirements without enough detail.
- Missing requirements are discovered late.
- Decisions made in meetings are lost.
- Reviewers lack the context behind a change.
- A feature is marked DONE in Rally but later becomes impacted by another change.
- Platform/security/library upgrades are treated as ordinary feature work even when they are not business requirements.
- Go-Live paperwork and compliance are prepared too late.
- Monitoring/alerting/runbooks are forgotten until deployment.
- Production knowledge does not feed back into engineering context.

Context Engineering addresses this by creating a persistent, connected Context Graph and generating context-specific views for each activity.

---
