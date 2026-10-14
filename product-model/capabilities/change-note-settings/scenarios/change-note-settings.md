---
kind: primary
routes:
  web: Web
steps:
- text: The Admin adds, renames, recolours or removes statuses in Notes and saves
  kind: actor
  actor: admin
  entities:
  - entity: configuration
    effect: reads
    facts:
    - Note statuses
  contexts:
    web:
      place: crm-web::administration::settings
- text: The Product saves the statuses
  kind: product
  actor: admin
  entities:
  - entity: configuration
    effect: changes
    facts:
    - Note statuses
  contexts:
    web:
      place: crm-web::administration::settings
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/settings/SettingsPage.tsx#SettingsPage
---

# Change note statuses

## Trigger

The team grades its contacts differently.

## Outcome

Notes and contact filters offer the new statuses.
