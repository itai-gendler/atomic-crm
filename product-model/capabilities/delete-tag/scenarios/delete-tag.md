---
kind: primary
routes:
  web: Web
steps:
- text: The Admin chooses Delete on a tag in the Tags section
  kind: actor
  actor: admin
  entities:
  - entity: tag
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: crm-web::administration::settings
- text: The Product deletes the tag and takes it off every contact, offering Undo for a few seconds
  kind: product
  actor: admin
  entities:
  - entity: tag
    effect: removes
  - entity: contact
    effect: changes
    facts:
    - Tags
  contexts:
    web:
      place: crm-web::administration::settings
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/settings/SettingsTags.tsx#SettingsTags
- kind: code
  role: implementation
  target: supabase/schemas/02_functions.sql#handle_tag_deleted
---

# Delete a tag

## Trigger

A tag is no longer used.

## Outcome

The tag is gone and no contact carries it; nothing else on those contacts changes.
