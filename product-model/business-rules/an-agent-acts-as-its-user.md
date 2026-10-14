---
appliesTo:
- type: capability
  id: query-crm-data
- type: capability
  id: mutate-crm-data
- type: capability
  id: approve-agent-access
references:
- kind: code
  role: implementation
  target: supabase/functions/mcp/index.ts
- kind: doc
  role: intent
  target: doc/src/content/docs/users/mcp-server.mdx
---

# An AI agent sees and changes only what its user may

Every query, change and completed task an AI agent sends runs as the user who approved it, after that approval.
