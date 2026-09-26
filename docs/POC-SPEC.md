# Context Graph POC — Requirements and Architecture Specification

**Version:** 0.1 (POC)  
**Status:** Prototype specification  
**Language:** English  
**Source baseline:** Shared conversation “Cải thiện Context Engineering” supplied by the user.

## 1. Executive overview

The Context Graph is a map of engineering reality: changes, requirements, design decisions, components, implementation intent, implementation, verification evidence, readiness, releases, operational signals, and follow-on changes. It links these records and their evidence without caching an entire codebase. Evidence carries provenance and temporal validity so a user can distinguish current facts from stale claims.

Rally sits outside the graph as a work-tracking projection. Rally cards represent engineering, release, or operational work. Rally is not the source of truth for engineering context. A completed Rally card does not reopen when new work appears; new work is represented by a new card and linked change/defect/incident.

This POC demonstrates the model and workflows with local sample data. It does not integrate with external systems.

## 2. Goals and non-goals

### Goals

1. Make a change and its cross-lifecycle impact understandable through linked graph entities.
2. Show source-backed evidence with origin, timestamp, confidence, and validity state.
3. Distinguish requirement, engineering change, defect, and incident.
4. Prepare compliance, quality, and operations readiness before release.
5. Present useful, role-specific context views for developers, reviewers, release owners, and operators.
6. Show Rally as a projection of actionable work while preserving the graph as context layer.
7. Support checkpoints that let a person resume work after a long pause.
8. Keep human decisions explicit; AI must not make decisions that require human judgment.
9. Work locally without MCP or CI.

### Non-goals

- Production integrations, authentication, multi-user collaboration, or authorization.
- Parsing arbitrary repositories or storing source code.
- Creating or synchronizing real Rally cards.
- Running CI, tests, security scans, deployments, or production monitoring.
- Autonomous AI decisions or recommendations presented as authoritative facts.
- Replacing Git/current code as the authority for implementation.

## 3. Users and roles

| Role | Primary question | POC view |
|---|---|---|
| Developer | What should I change and what implementation context matters? | Requirement, impact, component, implementation intent, verification |
| Reviewer | Is the implementation supported by evidence and within scope? | Change, affected components, decisions, evidence, open gates |
| Release owner | Is this change ready to release, and what remains unresolved? | Compliance, quality, operations, approvals, release checklist |
| Operator | What is deployed, how is it monitored, and how do I respond? | Release, alerts, dashboards, runbook, ownership, production feedback |

Roles are presentation filters in the POC, not security boundaries.

## 4. Architecture principles

1. **Context Graph = engineering reality.** The graph is the relationship/map layer.
2. **Evidence = source-backed truth.** Claims should link to a source and expose provenance and validity.
3. **Change = center of impact.** Analysis fans out from an engineering change to related systems and lifecycle records.
4. **Rally = work tracking.** Rally is a projection, not the engineering source of truth.
5. **Current code/Git = implementation authority.** The graph points to implementation context; it does not replace the repository.
6. **Do not cache the whole codebase.** Keep compact metadata, relationships, and references.
7. **Prepare operations early.** Monitoring, alerting, runbooks, dashboards, and ownership start before go-live.
8. **Production readiness has three dimensions:** compliance, quality, and operations.
9. **Human decisions stay human.** AI may summarize or surface gaps, but cannot silently approve or decide.
10. **No MCP or CI dependency.** The core model and local workflow are usable without either.
11. **Preserve temporal context.** Evidence can expire, be superseded, or be unknown.
12. **DONE work stays done.** A Rally card is not reopened to represent later work.

## 5. Conceptual architecture and lifecycle

```text
Business Change ─┐
Engineering Change ┼─> Impact Analysis -> Context Assessment
Production Feedback┘                          |
                          ┌────────────────────┼──────────────────┐
                          v                    v                  v
                    Experience Design   Solution Design   Operational Design
                          └────────────────────┼──────────────────┘
                                               v
                                      Component Design
                                               v
                                     Implementation Intent
                                               v
                                        Implementation
                                               v
                                    Verification / Evidence
                                               v
                                      Production Readiness
                                   Compliance | Quality | Operations
                                               v
                                            Release
                                               v
                                      Post-Go-Live Check
                                               v
                                           Production
                                               v
                                     Monitoring / Feedback
                                               v
                                      Change / Defect / Incident
                                               └──────> Context Graph

       Engineering Work / Release Work / Operational Work -> Rally projection
```

The POC models these as related records and lifecycle stages, not as an automated deployment pipeline.

## 6. Context Graph entity model

Every entity has an immutable `id`, `type`, `title`, `summary`, `status`, `createdAt`, `updatedAt`, and optional `owner`.

| Entity | Purpose | Example fields |
|---|---|---|
| BusinessChange | Business-originated outcome or policy change | requester, objective, due date |
| Requirement | Verifiable need or acceptance condition | statement, acceptance criteria, source |
| EngineeringChange | Unit of engineering impact and lifecycle coordination | scope, state, risk, target release |
| Defect | Confirmed product behavior gap | severity, observed behavior, expected behavior |
| Incident | Production disruption or operational event | impact, start/end, response owner |
| ContextAssessment | Human-reviewed understanding of affected context | scope, assumptions, unknowns, decision owner |
| DesignDecision | Chosen design and rationale | alternatives, rationale, decision status |
| Component | System boundary or code ownership unit | repository reference, owner, criticality |
| ImplementationIntent | Planned code/configuration change | approach, files or modules reference, Git link |
| Verification | Verification activity and outcome | method, result, run/reference |
| Evidence | Source-backed assertion | source, capturedAt, validFrom, validUntil, confidence, status |
| ReadinessGate | Compliance, quality, or operations criterion | category, state, evidence links, approver |
| Release | Deployment/release record | version, environment, date, state |
| OperationalAsset | Dashboard, alert, runbook, service owner | asset type, link, owner, readiness |
| Feedback | Post-release signal from production or users | source, severity, timestamp |
| RallyWorkItem | External-work projection metadata | card key, category, state, URL, sync state |
| Checkpoint | Resume marker for a person’s work | graph focus, last action, open questions, timestamp |

### Relationship types

- `originates_from`, `refines`, `implements`, `affects`, `depends_on`
- `decided_by`, `designed_for`, `implemented_by`, `verified_by`
- `supported_by`, `supersedes`, `validates`, `gates`
- `included_in_release`, `deployed_as`, `observed_in`, `caused_follow_up`
- `tracked_as` (graph entity to RallyWorkItem projection)
- `resumes_from` (checkpoint to focus entity)

Relationships have their own id, endpoints, type, createdAt, source/evidence references, and optional validity window.

## 7. Evidence and provenance requirements

An evidence item must include:

- **Source:** human-readable source name and reference/URI where available.
- **Captured time:** when the evidence was observed or recorded.
- **Validity:** valid-from and optional valid-until timestamps, or explicit unknown validity.
- **Status:** current, stale, superseded, disputed, or unverified.
- **Confidence:** an explanatory level, not an implicit approval.
- **Assertion:** what the evidence supports.
- **Related entities:** the graph facts and decisions it supports.

The UI must visibly distinguish current from stale/unknown evidence and never quietly promote an unverified assertion to confirmed truth. The POC uses sample evidence only.

## 8. Requirement discovery and change classification

The workflow starts by recording an incoming business change, requirement, engineering change, or production feedback. Users link origin and acceptance criteria, then classify subsequent work correctly:

- A **Requirement** states a need or constraint.
- An **Engineering Change** coordinates intended engineering impact.
- A **Defect** describes a product gap or incorrect behavior.
- An **Incident** records a production event and response.

These are separate entity types; linking them does not make them interchangeable.

## 9. Design and implementation flow

1. Capture origin, requirement, and acceptance criteria.
2. Create or select an Engineering Change as the impact-analysis center.
3. Assess affected components, dependencies, users, operational surfaces, assumptions, and unknowns.
4. Record experience, solution, and operational design decisions.
5. Define component-level design and implementation intent.
6. Reference current code/Git for actual implementation.
7. Link verification outcomes and source-backed evidence.
8. Evaluate readiness gates; unresolved gates remain visible.
9. Release only after an explicit human decision in this demo.
10. Record post-go-live checks, feedback, and follow-up change/defect/incident entities.

## 10. Production readiness

Readiness is the conjunction of three visible dimensions:

| Dimension | Representative requirements |
|---|---|
| Compliance | Security scan evidence, policy paperwork, required human approval |
| Quality | Tests, regression evidence, acceptance criteria verification |
| Operations | Monitoring, alerting, dashboard, runbook, service ownership |

Each gate has `not_started`, `in_progress`, `blocked`, or `complete` state and links to evidence. A change with incomplete mandatory gates cannot be represented as ready. In the POC, the readiness summary is computed from sample gate states; it does not certify actual readiness.

## 11. Monitoring, release, and feedback

Monitoring, alerting, dashboard, runbook, and ownership records are prepared from early design stages. The release record links the approved change, readiness evidence, environment, and post-go-live check. Production monitoring or user feedback can create new Feedback records and link to a new Change, Defect, or Incident. This creates a traceable loop back into the graph.

## 12. Rally integration/projection

The POC presents a Rally projection containing work category (engineering, release, operations), card key, state, and related graph entities. It is illustrative and has no live Rally connection.

Requirements:

- Graph entities remain the source context; Rally cards remain work-tracking references.
- Each projection points back to one or more graph entities.
- New work creates a new work item projection; completed cards are not reopened.
- No automatic write or sync occurs in this POC.

## 13. Context views

- **Developer:** change scope, impacted components, implementation intent, relevant evidence, verification.
- **Reviewer:** change rationale, design decisions, diffs/repository references, evidence validity, unresolved questions.
- **Release:** three readiness dimensions, blocking gates, approvals, target release, post-go-live plan.
- **Operations:** deployed version, service owner, dashboards, alerts, runbook, recent feedback, linked follow-up work.

Views filter and arrange the same graph data. They do not create separate copies of truth.

## 14. AI capabilities and human control

The architecture may later support AI summaries, relationship suggestions, impact-analysis drafts, missing-evidence detection, and checkpoint summaries. Such outputs must be labeled as generated suggestions and cite supporting graph evidence. AI must not decide requirement acceptance, risk acceptance, approvals, production readiness, release authorization, or incident severity on behalf of an accountable human. The current POC uses deterministic sample text and has no AI model.

## 15. Local CLI architecture and deployment assumptions

Core model: local static web application with embedded sample records and browser local storage. No server, MCP tool, CI pipeline, or external connector is required. Git/repository references are metadata only. A later CLI may import/export graph snapshots and checkpoints, but no CLI is in this POC scope.

## 16. Checkpoint and resume

A checkpoint captures timestamp, focused entity, active role/view, completed work summary, unresolved questions, and next suggested action. Resume restores the focus and presents the open questions. Checkpoint creation is user initiated. Stored in local browser storage in the POC.

## 17. Functional requirements

| ID | Requirement | POC verification |
|---|---|---|
| FR-01 | Show a lifecycle map from change origin through production feedback | Lifecycle board displays stages and linked sample records |
| FR-02 | Center impact analysis on an Engineering Change | Selecting a change shows affected entities and links |
| FR-03 | Preserve distinct Requirement, Change, Defect, and Incident types | Seed data and detail panel identify distinct types |
| FR-04 | Inspect graph entities and typed relationships | Selecting an entity exposes related records |
| FR-05 | Display evidence source, capture time, validity, status, and confidence | Evidence panel renders all metadata |
| FR-06 | Surface stale, disputed, unverified, or unknown evidence | Non-current evidence is visually marked |
| FR-07 | Represent production readiness across Compliance, Quality, Operations | Three separate gate groups and summary are shown |
| FR-08 | Keep monitoring, alerting, dashboard, runbook, and owner visible before release | Operations assets appear in design/readiness stages |
| FR-09 | Require explicit human action to advance gated lifecycle state | UI explains blockers and requires a user action |
| FR-10 | Present Rally as a linked work projection | Rally view shows card keys and graph references |
| FR-11 | Preserve DONE work items when later work is created | Follow-up is represented separately in sample model/UI |
| FR-12 | Provide role-specific context views | User can switch four views |
| FR-13 | Create and resume a checkpoint | Checkpoint can be saved locally and restored |
| FR-14 | Operate without MCP, CI, or external services | Static application loads from workspace |
| FR-15 | Avoid caching full source code | Only reference strings and metadata are stored |
| FR-16 | Keep all interface and specification text in English | All POC UI and docs use English |

## 18. Non-functional requirements

- **Local-first:** no network request required for core demo behavior.
- **Understandable provenance:** source and validity are visible where evidence is used.
- **Reversible demo state:** local data can be reset through the UI.
- **Responsive:** usable on common desktop and tablet widths.
- **Accessible basics:** semantic controls, keyboard-focusable interactions, labels, and status text not conveyed by color alone.
- **Small footprint:** no framework or dependency installation required.
- **Honest status:** illustrative/sample content is clearly labeled.

## 19. End-to-end example

Sample story: a product owner requests a checkout latency improvement. The Requirement defines a measurable latency target and acceptance criteria. An Engineering Change links the requirement and identifies checkout API and telemetry components. Context assessment records downstream consumers and uncertainty about a legacy client. Solution and operational designs describe a query/index adjustment, dashboard metric, alert threshold, rollback procedure, and service owner. Implementation intent links to a Git reference; verification evidence records unit, regression, and performance results with source and dates. Compliance, Quality, and Operations gates are reviewed by accountable humans. A release record links the approved change. Post-go-live monitoring records a latency observation. If an alert fires, a new Incident and operations work item are created; the completed release card remains done. Every fact is linked back through the graph.

The POC ships a compact seeded example of this story, with sample values explicitly marked as demo data.

## 20. Acceptance criteria

The POC is acceptable when:

1. A user can open it locally without installing packages or configuring integrations.
2. The lifecycle and role views expose the same connected example data.
3. A user can follow a change to its requirements, components, design, implementation reference, verification, readiness gates, release, operations assets, and feedback.
4. Evidence details make origin and temporal validity apparent.
5. Incomplete readiness is visibly blocked and cannot be mistaken for approval.
6. Rally is shown as a projection and completed work is not reopened for follow-up work.
7. A checkpoint can be saved and resumed from browser storage.
8. No AI, MCP, CI, repository, Rally, or production connection is implied to exist.
9. Interface labels, instructions, and specification are entirely in English.

## 21. Risks, assumptions, and next decisions

- All seed entities, sources, and metrics are illustrative; they must be replaced before using this model for real delivery decisions.
- Browser local storage is per-browser and not shared or backed up.
- The exact Rally field mapping, repository metadata strategy, evidence retention policy, and identity/ownership model require stakeholder decisions before integration work.
- Production deployment, permissions, audit history, graph persistence, and connector reliability are intentionally unresolved.
- The current POC proves interaction and information architecture only; it does not validate organizational workflow or data quality.

## 22. Traceability to the shared baseline

This specification captures the shared-chat commitments: Context Graph as the engineering reality map; evidence as source-backed truth; change-centered impact; Rally as work tracking; DONE cards not reopened; separate requirement/change/defect/incident types; early operational preparation; compliance + quality + operations readiness; human control for AI decisions; no MCP/CI dependency; Git/current code as implementation authority; provenance and temporal validity; no full-code cache; checkpoints for resuming; and the 20 architecture sections proposed in the chat.

