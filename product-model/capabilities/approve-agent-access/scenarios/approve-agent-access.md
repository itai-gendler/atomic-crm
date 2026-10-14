---
kind: primary
routes:
  web: Web
steps:
- text: The User reads which AI agent asks for access and with what scope
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
- text: The User chooses Approve
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace::agent-access
- text: The Product records the approval and returns the User to the AI agent
  kind: product
  actor: user
  entities:
  - entity: ai-agent-access
    effect: creates
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
references:
- kind: code
  role: implementation
  target: src/components/supabase/oauth-consent-page.tsx#OAuthConsentPage
- kind: doc
  role: intent
  target: doc/src/content/docs/users/mcp-server.mdx
---

# Approve an AI agent

## Trigger

A User connects an AI assistant to the CRM's MCP server.

## Outcome

The AI agent can use the MCP server as that User.

## Edge cases

- An agent the User already approved skips the consent page and returns at once.
- A person who is not signed in signs in first and comes back to the consent page.
