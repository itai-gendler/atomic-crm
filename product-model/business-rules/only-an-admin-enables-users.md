---
appliesTo:
- type: entity
  id: user-account
  effect: changes
  to: Active
permits:
- actors:
  - admin
references:
- kind: code
  role: implementation
  target: supabase/functions/users/index.ts
---

# Only an Admin enables a user

Enabling a disabled account is an Admin's decision.
