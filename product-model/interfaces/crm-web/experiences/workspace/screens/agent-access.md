---
entities:
- entity: ai-agent-access
  shows:
  - Agent name
  - Redirect address
  - Access scope
  collects:
  - Agent name
  - Redirect address
  - Access scope
entryPoints:
- crm-web: /oauth/consent
---

# AI agent access

Where a signed-in user approves or denies an AI agent's request.
