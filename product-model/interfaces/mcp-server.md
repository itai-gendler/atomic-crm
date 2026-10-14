---
type: agent
actors:
- ai-agent
references:
- kind: code
  role: implementation
  target: supabase/functions/mcp/index.ts
- kind: doc
  role: intent
  target: doc/src/content/docs/users/mcp-server.mdx
---

# MCP server

The Model Context Protocol server through which a person's AI assistant reads and changes the CRM's data on their behalf, after they approve it.
