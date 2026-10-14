---
kind: primary
routes:
  web: Web
steps:
- text: The User reads which AI agent asks for access
  kind: actor
  actor: user
  entities:
  - entity: ai-agent-access
    effect: reads
    facts:
    - Agent name
    - Redirect address
    - Access scope
  - entity: ai-agent
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::agent-access
- text: The User chooses Deny
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace::agent-access
- text: The Product returns the User to the AI agent with a refusal
  kind: product
  actor: user
  entities:
  - entity: ai-agent
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::agent-access
references:
- kind: code
  role: implementation
  target: src/components/supabase/oauth-consent-page.tsx#OAuthConsentPage
---

# Deny an AI agent

## Trigger

A User does not want an AI assistant to reach the CRM.

## Outcome

The AI agent gets no access.
