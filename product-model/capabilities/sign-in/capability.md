---
availability:
- place: crm-web::sign-in
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/login/LoginPage.tsx#LoginPage
- kind: code
  role: implementation
  target: src/components/atomic-crm/providers/supabase/authProvider.ts#getAuthProvider
---

# Sign in

Enter the CRM with an email and password, or through Google Workspace single sign-on where the deployment configures a Workspace domain. A deployment may also turn password sign-in off, leaving single sign-on only.
