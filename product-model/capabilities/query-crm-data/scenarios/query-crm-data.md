---
kind: primary
routes:
  agent: MCP server
steps:
- text: The AI agent asks for the database schema
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp-server
- text: The AI agent sends a single read-only query, such as the open deals above a budget
  kind: actor
  actor: ai-agent
  entities:
  - entity: deal
    effect: reads
    facts: []
  contexts:
    agent:
      place: mcp-server
- text: The Product runs it as the connected user and returns the rows
  kind: product
  actor: ai-agent
  entities:
  - entity: deal
    effect: reads
    facts:
    - Name
    - Stage
    - Budget
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
  target: supabase/functions/mcp/validateSql.ts#validateReadOnly
---

# An AI agent reads CRM data

## Trigger

A person asks their AI assistant about their CRM.

## Outcome

The agent has the data to answer.
