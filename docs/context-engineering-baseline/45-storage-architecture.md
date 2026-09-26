# 45. Storage Architecture

The architecture should separate:

```text
Source Evidence
      │
      ▼
Evidence Store
      │
      ▼
Context Knowledge
      │
      ▼
Context Graph
      │
      ▼
Retrieval / Context Views
```

Possible logical storage layers:

### Raw Evidence

Stores original artifacts or references:

- Documents
- Meeting transcripts
- Emails
- Screenshots
- Git references
- Test evidence
- Security evidence
- Monitoring evidence

### Structured Context

Stores:

- Entities
- Relationships
- Status
- Decisions
- Requirements
- Dependencies
- Impacts

### Retrieval Index

Supports:

- Semantic search
- Keyword search
- Relationship retrieval
- Code search
- Context retrieval

The exact technology is an implementation choice.

The conceptual separation is more important.

---
