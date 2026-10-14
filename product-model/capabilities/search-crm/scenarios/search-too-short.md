---
kind: edge
routes:
  web: Web
steps:
- text: The User types a single character
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace::global-search
- text: The Product asks for at least two characters and searches nothing
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace::global-search
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/search/searchModel.ts
---

# A one-letter search waits for more

## Trigger

A User starts typing.

## Outcome

No results are shown yet.
