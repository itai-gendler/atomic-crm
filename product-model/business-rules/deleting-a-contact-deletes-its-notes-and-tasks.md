---
appliesTo:
- type: capability
  id: delete-contact
- type: entity
  id: contact
  effect: removes
references:
- kind: code
  role: implementation
  target: supabase/schemas/01_tables.sql
---

# Deleting a contact deletes its notes and tasks

A contact's notes and tasks are removed with it.
