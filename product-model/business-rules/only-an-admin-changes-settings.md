---
appliesTo:
- type: entity
  id: configuration
  effect: changes
permits:
- actors:
  - admin
references:
- kind: code
  role: implementation
  target: supabase/schemas/05_policies.sql
- kind: code
  role: implementation
  target: src/components/atomic-crm/providers/commons/canAccess.ts#canAccess
---

# Only an Admin changes the settings

Branding and the lists of sectors, stages, categories, statuses and types are shared by the whole team and changed by an Admin.
