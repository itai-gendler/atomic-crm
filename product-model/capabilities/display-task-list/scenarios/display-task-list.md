---
kind: primary
routes:
  agent: MCP server
steps:
- text: The AI agent passes tasks it queried, with their contacts, to the task list tool
  kind: actor
  actor: ai-agent
  entities:
  - entity: contact
    effect: reads
    facts: []
  - entity: task
    effect: reads
    facts: []
  contexts:
    agent:
      place: mcp-server
- text: The Product renders them as a list with a mark-as-done button per task and a link to each contact's page in the CRM
  kind: product
  actor: ai-agent
  entities:
  - entity: task
    effect: reads
    facts:
    - Description
    - Type
    - Due date
    - Done date
    - Contact
  - entity: contact
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
  target: supabase/functions/mcp/taskListUi.ts
---

# An AI agent shows a task list

## Trigger

A person asks their AI assistant for their pending tasks.

## Outcome

The person sees an actionable task list in the agent.
