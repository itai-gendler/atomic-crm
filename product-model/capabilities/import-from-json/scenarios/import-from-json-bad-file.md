---
kind: edge
routes:
  web: Web
steps:
- text: The User uploads a file that is not valid JSON
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace::json-import
- text: The Product reports that it is unable to import this file
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace::json-import
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/misc/ImportPage.tsx
---

# An unreadable file is refused

## Trigger

The chosen file cannot be read.

## Outcome

Nothing is imported.
