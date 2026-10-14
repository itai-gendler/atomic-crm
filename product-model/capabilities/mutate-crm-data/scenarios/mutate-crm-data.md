---
kind: primary
routes:
  agent: MCP server
steps:
- text: The AI agent sends a single update moving a deal to the won stage
  kind: actor
  actor: ai-agent
  entities:
  - entity: deal
    effect: reads
    facts:
    - Name
  contexts:
    agent:
      place: mcp-server
- text: The Product runs it as the connected user and returns the result
  kind: product
  actor: ai-agent
  entities:
  - entity: deal
    effect: changes
    facts:
    - Stage
  - entity: user
    effect: reads
    facts: []
  contexts:
    agent:
      place: mcp-server
references:
- kind: code
  role: implementation
  target: supabase/functions/mcp/index.ts
- kind: code
  role: implementation
  target: supabase/functions/mcp/validateSql.ts#validateWrite
---

# An AI agent updates a deal

## Trigger

A person tells their AI assistant a deal was won.

## Outcome

The deal is in the won stage.
