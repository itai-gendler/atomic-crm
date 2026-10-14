---
appliesTo:
- type: capability
  id: delete-company
- type: entity
  id: company
  effect: removes
references:
- kind: code
  role: implementation
  target: supabase/schemas/01_tables.sql
---

# Deleting a company deletes its contacts and deals

Every contact working at the company, with its notes and tasks, and every deal made with the company, with its notes, goes with it.
