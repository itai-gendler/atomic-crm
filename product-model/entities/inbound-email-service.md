---
kind: system
acts: external
references:
- kind: code
  role: implementation
  target: supabase/functions/postmark/index.ts
- kind: doc
  role: intent
  target: doc/src/content/docs/developers/inbound-email-configuration.mdx
---

# Inbound email service

The email service that receives mail sent or forwarded to the CRM's inbound address and posts each message to the CRM.
