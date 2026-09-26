# 31. Context Checkpoint

Context Checkpoint exists to solve the problem:

> "I haven't touched this area for several weeks. What has changed and what do I need to know before continuing?"

A checkpoint records the relevant state at a point in time.

```text
ContextCheckpoint
├── business_state
├── requirement_state
├── design_state
├── implementation_state
├── test_state
├── release_state
├── operational_state
├── open_questions
├── active_risks
├── pending_decisions
└── timestamp
```

When resuming work:

```text
Last Checkpoint
      +
Changes Since Checkpoint
      +
Current Relevant Context
      +
Open Questions
      +
Active Risks
      +
Pending Decisions
      ↓
Resume Context
```

The objective is to avoid rereading the entire repository, meeting history, Confluence, emails, and design documents.

---
