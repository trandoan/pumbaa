# Context Graph POC

This workspace is a documentation and sample-data scaffold for the Context Graph proof of concept. It intentionally contains no application implementation.

## Repository layout

```text
.
├── README.md
├── docs/
│   └── POC-SPEC.md
├── schemas/
│   ├── checkpoint.schema.json
│   ├── context-graph.schema.json
│   ├── entity.schema.json
│   ├── evidence.schema.json
│   └── relationship.schema.json
├── samples/
│   ├── checkpoint.json
│   ├── context-graph.json
│   ├── evidence.json
│   └── rally-projection.json
└── templates/
    ├── change-record.json
    ├── checkpoint.json
    └── evidence-record.json
```

## Start here

1. Read [`docs/POC-SPEC.md`](docs/POC-SPEC.md) for scope, architecture, requirements, and acceptance criteria.
2. Review the JSON contracts in `schemas/`.
3. Use the illustrative records in `samples/` to understand the links between entities.
4. Copy a matching file from `templates/` when drafting a new record.

All sample values are fictional and illustrative. Repository and source references are examples; no external system is connected. Files in this scaffold are written in English.

