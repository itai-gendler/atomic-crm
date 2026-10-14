---
appliesTo:
- type: entity
  id: company
  effect: creates
- type: entity
  id: contact
  effect: creates
- type: entity
  id: contact-note
  effect: creates
- type: entity
  id: deal
  effect: creates
- type: entity
  id: deal-note
  effect: creates
- type: entity
  id: activity
references:
- kind: code
  role: implementation
  target: supabase/schemas/03_views.sql
---

# The activity log shows every company, contact, note and deal added

Each addition appears in the activity log with its date, the user who added it and its company.
