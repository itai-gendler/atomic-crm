---
type: webhook
actors:
- inbound-email-service
references:
- kind: code
  role: implementation
  target: supabase/functions/postmark/index.ts
- kind: doc
  role: intent
  target: doc/src/content/docs/developers/inbound-email-configuration.mdx
---

# Inbound email

The webhook the inbound email service posts each email received at the CRM's inbound address to, protected by its own credentials. Exists where the deployment sets up an inbound address.
