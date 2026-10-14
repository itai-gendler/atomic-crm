---
kind: primary
routes:
  web: Web
steps:
- text: The User drops a JPEG or PNG on the avatar editor, frames it and chooses Update Image
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace::profile
- text: The Product saves the picture as the User's avatar
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
- kind: code
  role: implementation
  target: src/components/atomic-crm/settings/ProfilePage.tsx#ProfilePage
---

# Upload a new avatar

## Trigger

A User wants their face next to their notes.

## Outcome

The new avatar shows across the CRM.
