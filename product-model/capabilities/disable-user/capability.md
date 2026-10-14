---
domain: users
availability:
- place: crm-web::administration
references:
- kind: code
  role: implementation
  target: supabase/functions/users/index.ts
---

# Disable user

Stop a user from using the CRM without deleting anything they own: users are disabled, never deleted.
