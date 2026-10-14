---
domain: contacts
availability:
- place: crm-web::workspace
references:
- kind: code
  role: implementation
  target: supabase/functions/merge_contacts/index.ts
- kind: doc
  role: intent
  target: doc/src/content/docs/users/merging-contacts.mdx
---

# Merge contacts

Fold a duplicate contact into another one. The contact being merged is deleted; its notes, tasks and deals move to the kept contact.
