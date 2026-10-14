---
appliesTo:
- type: entity
  id: user-account
  effect: removes
permits: []
references:
- kind: doc
  role: intent
  target: AGENTS.md
- kind: code
  role: implementation
  target: supabase/schemas/05_policies.sql
---

# No one deletes a user

A user account is disabled instead, so the contacts, deals and notes it manages or wrote are never lost.
