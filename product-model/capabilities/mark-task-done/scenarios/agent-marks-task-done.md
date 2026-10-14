---
kind: primary
routes:
  agent: MCP server
steps:
- text: The AI agent asks to mark a task done by its id
  kind: actor
  actor: ai-agent
  entities:
  - entity: task
    effect: reads
    facts: []
  contexts:
    agent:
      place: mcp-server
- text: The Product marks the task done now and confirms it
  kind: product
  actor: ai-agent
  entities:
  - entity: task
    effect: changes
    from: Pending
    to: Done
    facts:
    - Done date
  contexts:
    agent:
      place: mcp-server
references:
- kind: code
  role: implementation
  target: supabase/functions/mcp/index.ts
---

# An AI agent ticks a task off

## Trigger

A person clicks a task's checkmark in the agent's task list, or asks the agent to close a task.

## Outcome

The task is done in the CRM.
