# 41. Technical Architecture Direction

The architecture does not depend on MCP.

It also does not depend on CI controlled by the team.

A practical implementation can use local/on-demand mechanisms:

```text
Git
  +
ripgrep
  +
AST analysis
  +
Symbol analysis
  +
Dependency analysis
  +
OpenAPI parsing
  +
Event schema parsing
  +
Local CLI
  +
Local cache
```

Repository analysis can be performed on demand.

---
