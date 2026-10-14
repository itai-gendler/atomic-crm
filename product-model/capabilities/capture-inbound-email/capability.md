---
availability:
- place: inbound-email
references:
- kind: code
  role: implementation
  target: supabase/functions/postmark/index.ts
---

# Capture email

Turn an email a user sends with the CRM's inbound address in copy, or forwards to it, into a note on the contact of each recipient in To, creating the contact and its company when unknown. Exists only where the deployment sets up an inbound email address.
