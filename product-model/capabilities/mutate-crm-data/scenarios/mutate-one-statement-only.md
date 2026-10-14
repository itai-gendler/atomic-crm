---
kind: validation
routes:
  agent: MCP server
steps:
- text: The AI agent sends several statements, or one that is not an insert, update or delete
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp-server
- text: The Product refuses it and runs nothing
  kind: product
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp-server
references:
- kind: code
  role: implementation
  target: supabase/functions/mcp/validateSql.ts#validateWrite
---

# Several statements are refused

## Trigger

An agent batches statements.

## Outcome

Nothing runs.
