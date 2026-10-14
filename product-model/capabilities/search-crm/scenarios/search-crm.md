---
kind: primary
routes:
  web: Web
steps:
- text: The User opens the search from the top bar, or with Ctrl+K, and types at least two characters
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace::global-search
- text: The Product lists up to fifty matching records, most recent first, highlighting the matched words and quoting the field that matched
  kind: product
  actor: user
  entities:
  - entity: company
    effect: reads
    facts:
    - Name
    - Sector
    - Description
    - Website
  - entity: contact
    effect: reads
    facts:
    - First name
    - Last name
    - Title
    - Background
    - Email addresses
    - Phone numbers
  - entity: deal
    effect: reads
    facts:
    - Name
    - Category
    - Description
  - entity: task
    effect: reads
    facts:
    - Description
    - Type
  - entity: contact-note
    effect: reads
    facts:
    - Text
    - Attachments
  - entity: deal-note
    effect: reads
    facts:
    - Text
    - Attachments
  contexts:
    web:
      place: crm-web::workspace::global-search
- text: The User opens a result
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace::global-search
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/search/GlobalSearchButton.tsx
- kind: code
  role: implementation
  target: supabase/schemas/08_search.sql
- kind: doc
  role: intent
  target: doc/src/content/docs/users/global-search.mdx
---

# Search across the CRM

## Trigger

A User remembers a word but not where it is.

## Outcome

The User is on the page of the record found.

## Edge cases

- Every word typed must start a word of the same record.
- Archived deals, done tasks and notes of archived deals are left out.
- On a phone, deals and deal notes are not offered.
