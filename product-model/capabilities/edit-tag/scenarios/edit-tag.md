---
kind: primary
routes:
  web: Web
steps:
- text: The Admin chooses Edit on a tag in the Tags section and changes its name or colour
  kind: actor
  actor: admin
  entities:
  - entity: tag
    effect: reads
    facts:
    - Name
    - Color
  contexts:
    web:
      place: crm-web::administration::settings
- text: The Product saves the tag at once
  kind: product
  actor: admin
  entities:
  - entity: tag
    effect: changes
    facts:
    - Name
    - Color
  contexts:
    web:
      place: crm-web::administration::settings
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/settings/SettingsTags.tsx#SettingsTags
- kind: code
  role: implementation
  target: src/components/atomic-crm/tags/TagEditModal.tsx
---

# Edit a tag

## Trigger

A tag's name or colour no longer fits.

## Outcome

Every contact with the tag shows its new name and colour.
