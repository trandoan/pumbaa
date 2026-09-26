# 5. Evidence Model

Evidence is first-class.

## Raw Evidence Sources

Examples:

- Confluence
- Figma
- Meeting transcript/notes
- Email
- Screenshot/image/OCR
- Git commit/diff
- Test execution/log
- Snyk scan
- Platform/security notice
- Production monitoring
- Incident record

Raw evidence remains the source for what was actually stated or observed.

## Derived Knowledge

```text
Evidence
   ↓
Extraction
   ↓
Structured Knowledge
   ↓
Context Graph
```

Derived knowledge must preserve:

- Source/provenance
- Timestamp
- Validity
- Confidence where appropriate
- Fact vs decision vs assumption vs inference

Never silently convert inference into fact.

Example:

```text
Meeting:
"Maybe use Kafka"

≠

Decision:
"We will use Kafka"

≠

Implementation Evidence:
"Service publishes to Kafka"
```

## Temporal Validity

Do not overwrite history.

Knowledge may be:

- CURRENT
- SUPERSEDED
- UNDER_REVIEW
- HISTORICAL
- ARCHIVED

Current implementation authority remains Git/current source.

---
