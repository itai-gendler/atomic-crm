---
availability:
- place: crm-web::workspace
references:
- kind: code
  role: implementation
  target: src/components/supabase/oauth-consent-page.tsx#OAuthConsentPage
---

# Approve AI agent access

Let an AI agent use the CRM through the MCP server on one's behalf. The agent's connection flow brings the person to the CRM's consent page, signed in first if needed.
