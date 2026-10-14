---
appliesTo:
- type: capability
  id: query-crm-data
- type: capability
  id: mutate-crm-data
references:
- kind: code
  role: implementation
  target: supabase/functions/mcp/validateSql.ts
---

# An AI agent runs one SQL statement per call

The query tool accepts one read-only statement and the mutate tool one insert, update or delete.
