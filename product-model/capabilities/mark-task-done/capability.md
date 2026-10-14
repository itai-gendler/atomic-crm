---
availability:
- place: crm-web::workspace
- place: mcp-server
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/tasks/Task.tsx#Task
- kind: code
  role: implementation
  target: supabase/functions/mcp/index.ts
---

# Mark task done

Tick a task off, from the CRM or through an AI agent.
