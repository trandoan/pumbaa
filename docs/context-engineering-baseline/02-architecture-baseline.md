# 2. Architecture Baseline

```text
                         CONTEXT GRAPH
                               │
       ┌───────────────────────┼───────────────────────┐
       │                       │                       │
       ▼                       ▼                       ▼
 BUSINESS CHANGE         ENGINEERING CHANGE      PROD FEEDBACK
       │                       │                       │
       └───────────────────────┼───────────────────────┘
                               ▼
                        IMPACT ANALYSIS
                               │
                       CONTEXT ASSESSMENT
                               │
              ┌────────────────┼────────────────┐
              ▼                ▼                ▼
         EXPERIENCE         SOLUTION       OPERATIONAL
           DESIGN            DESIGN           DESIGN
              │                │                │
              └────────────────┼────────────────┘
                               ▼
                        COMPONENT DESIGN
                               ▼
                     IMPLEMENTATION INTENT
                               ▼
                         IMPLEMENTATION
                               ▼
                    VERIFICATION / EVIDENCE
                               ▼
                    PRODUCTION READINESS
                               │
                 ┌─────────────┼─────────────┐
                 ▼             ▼             ▼
             COMPLIANCE      QUALITY      OPERATIONS
             Snyk/Security   Testing      Monitoring
             Paperwork       Evidence     Alerting
             Approval        Regression   Dashboard
                                          Runbook
                                          Ownership
                 └─────────────┼─────────────┘
                               ▼
                            RELEASE
                               ▼
                     POST-GO-LIVE CHECK
                               ▼
                              PROD
                               │
                       ┌───────┴────────┐
                       ▼                ▼
                   MONITORING        FEEDBACK
                       │                │
                       └───────┬────────┘
                               ▼
                         CHANGE / DEFECT
                               │
                               └────────→ CONTEXT GRAPH
```

**Important:** Context Graph is **not one SDLC step**. It surrounds and connects all activities.

---
