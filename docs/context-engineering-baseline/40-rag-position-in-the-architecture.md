# 40. RAG Position in the Architecture

RAG means:

> Retrieval-Augmented Generation.

RAG is a **retrieval mechanism**, not the architecture itself.

The architecture is:

```text
Business Outcome
      │
      ▼
Context Graph
      │
      ├── Structured Knowledge
      ├── Evidence
      ├── Current Code
      └── Relationships
              │
              ▼
        Retrieval Layer
              │
       ┌──────┴──────┐
       ▼             ▼
 Structured       Semantic
 Retrieval        Retrieval
       │             │
       └──────┬──────┘
              ▼
       Context Resolver
              │
              ▼
       Context View
              │
              ▼
 Cursor / Developer / Reviewer /
 Release / Operations
```

Structured retrieval is appropriate for:

- Entities
- Relationships
- Dependencies
- APIs
- Events
- Code references
- Status
- Impact
- Version
- Temporal state

Semantic retrieval is appropriate for:

- Confluence
- Meetings
- Email
- Unstructured documents
- Notes
- OCR
- Screenshots

RAG does not establish truth.

It only retrieves information.

Truth comes from:

- Provenance
- Source authority
- Temporal validity
- Evidence
- Explicit decisions
- Current implementation

---
