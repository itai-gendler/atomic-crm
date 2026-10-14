---
appliesTo:
- type: capability
  id: create-contact
- type: capability
  id: create-company
- type: capability
  id: create-deal
- type: capability
  id: add-task
references:
- kind: code
  role: implementation
  target: supabase/schemas/02_functions.sql#set_sales_id_default
- kind: code
  role: implementation
  target: supabase/schemas/04_triggers.sql
---

# Whoever creates a record manages it unless another user is chosen

New contacts and companies default to their creator as account manager; deals, notes and tasks belong to their creator.
