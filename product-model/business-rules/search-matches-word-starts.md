---
appliesTo:
- type: capability
  id: search-crm
  contexts:
  - place: crm-web::workspace
references:
- kind: code
  role: implementation
  target: supabase/schemas/08_search.sql
- kind: doc
  role: intent
  target: doc/src/content/docs/users/global-search.mdx
---

# Search matches the start of every word typed

Every word must start a word of the same record, accents and case aside; results are capped at fifty, newest first.
