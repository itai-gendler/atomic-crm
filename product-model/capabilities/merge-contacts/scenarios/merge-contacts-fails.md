---
kind: edge
routes:
  web: Web
steps:
- text: The User confirms Merge Contacts
  kind: actor
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::contact
- text: The merge cannot be completed
  kind: condition
  entities:
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::contact
- text: The Product reports that the contacts could not be merged and leaves both as they were
  kind: product
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::contact
references:
- kind: code
  role: implementation
  target: supabase/functions/merge_contacts/index.ts
---

# A failed merge changes nothing

## Trigger

The merge fails part-way.

## Outcome

Both contacts are unchanged.
