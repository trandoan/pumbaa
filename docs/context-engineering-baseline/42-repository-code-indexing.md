# 42. Repository / Code Indexing

Repositories should not be treated as static documents.

Code changes frequently.

Therefore:

> Current source is the implementation authority.

A catalog may store:

- Repository
- Service
- Components
- APIs
- Events
- Dependencies
- Important symbols
- Configuration
- Ownership
- Relationships

But:

> Catalog is a map, not a cache.

Do not make a brittle exact-file inventory the primary truth.

Instead:

```text
Repository
   │
   ▼
Current Git State
   │
   ▼
Dynamic Code Analysis
   │
   ├── AST
   ├── Symbols
   ├── Imports
   ├── Dependencies
   ├── API contracts
   └── Event contracts
```

Analysis results can be cached using:

```text
Repository + Commit SHA
```

This allows reuse without assuming that the code remains unchanged.

---
