---
appliesTo:
- type: capability
  id: edit-profile
- type: entity
  id: user-account
  facts:
  - Secondary emails
references:
- kind: code
  role: implementation
  target: supabase/functions/users/secondaryEmails.ts
---

# A user has at most ten secondary emails

Secondary emails are stored lowercased and without duplicates, and each must be an email address.
