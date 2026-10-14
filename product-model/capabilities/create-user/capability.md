---
domain: users
availability:
- place: crm-web::administration
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/sales/SalesCreate.tsx#SalesCreate
- kind: code
  role: implementation
  target: supabase/functions/users/index.ts
---

# Create user

Add a member of the sales team. The new person receives an email to set their password.
