---
kind: validation
routes:
  agent: MCP server
steps:
- text: The AI agent sends a statement that changes data, or several statements, to the query tool
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp-server
- text: The Product refuses it and points to the mutate tool
  kind: product
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp-server
references:
- kind: code
  role: implementation
  target: supabase/functions/mcp/validateSql.ts#validateReadOnly
---

# A query that writes is refused

## Trigger

An agent uses the read tool to write.

## Outcome

Nothing runs.
