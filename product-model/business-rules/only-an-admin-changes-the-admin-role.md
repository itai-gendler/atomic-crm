---
appliesTo:
- type: entity
  id: user-account
  effect: changes
  facts:
  - Admin
permits:
- actors:
  - admin
references:
- kind: code
  role: implementation
  target: supabase/functions/users/index.ts
---

# Only an Admin grants or revokes the Admin role

Whether an account holds the Admin role is changed by an Admin only.
