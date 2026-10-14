---
appliesTo:
- type: entity
  id: user-account
  effect: changes
  facts:
  - Password
permits:
- actors:
  - visitor
references:
- kind: code
  role: implementation
  target: src/components/supabase/set-password-page.tsx#SetPasswordPage
- kind: code
  role: implementation
  target: supabase/functions/update_password/index.ts
---

# A password is set only by following a link emailed to the account

Invitations and password resets both email a link; the password is chosen on the page that link opens, never in the profile or by an Admin.
