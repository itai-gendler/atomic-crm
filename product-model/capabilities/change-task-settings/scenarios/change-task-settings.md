---
kind: primary
routes:
  web: Web
steps:
- text: The Admin adds, renames or removes types in Tasks and saves
  kind: actor
  actor: admin
  entities:
  - entity: configuration
    effect: reads
    facts:
    - Task types
  - entity: task
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::administration::settings
- text: The Product saves the task types
  kind: product
  actor: admin
  entities:
  - entity: configuration
    effect: changes
    facts:
    - Task types
  - entity: task
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::administration::settings
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/settings/SettingsPage.tsx#SettingsPage
---

# Change task types

## Trigger

The team tracks new kinds of follow-up.

## Outcome

Task forms offer the new types.
