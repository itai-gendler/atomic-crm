---
kind: edge
routes:
  agent: MCP server
steps:
- text: The AI agent asks to mark a task done by an id
  kind: actor
  actor: ai-agent
  entities:
  - entity: task
    effect: reads
    facts: []
  contexts:
    agent:
      place: mcp-server
- text: No task with that id is reachable
  kind: condition
  entities:
  - entity: task
    effect: reads
    facts: []
  contexts:
    agent:
      place: mcp-server
- text: The Product answers that the task was not found and changes nothing
  kind: product
  actor: ai-agent
  entities:
  - entity: task
    effect: reads
    facts: []
  contexts:
    agent:
      place: mcp-server
references:
- kind: code
  role: implementation
  target: supabase/functions/mcp/index.ts
---

# An unknown task is reported

## Trigger

The agent names a task that does not exist.

## Outcome

Nothing changes.
