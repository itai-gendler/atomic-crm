---
appliesTo:
- type: entity
  id: user-account
  effect: changes
  to: Disabled
permits:
- actors:
  - admin
references:
- kind: code
  role: implementation
  target: supabase/functions/users/index.ts
---

# Only an Admin disables a user

Disabling an account is an Admin's decision.
