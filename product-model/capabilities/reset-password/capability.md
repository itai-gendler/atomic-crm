---
availability:
- place: crm-web::sign-in
- place: crm-web::workspace
references:
- kind: code
  role: implementation
  target: src/components/supabase/forgot-password-page.tsx
- kind: code
  role: implementation
  target: src/components/supabase/set-password-page.tsx#SetPasswordPage
---

# Reset password

Choose a new password through a link sent by email, asked for from the sign-in page (Forgot password?) or from one's profile (Change password).
