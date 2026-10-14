---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Delete in the avatar editor
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace::profile
- text: The Product removes the User's picture
  kind: product
  actor: user
  entities:
  - entity: user-account
    effect: changes
    facts:
    - Avatar
  contexts:
    web:
      place: crm-web::workspace::profile
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/misc/ImageEditorField.tsx
---

# Delete the avatar

## Trigger

A User no longer wants a picture.

## Outcome

The User has no avatar.
