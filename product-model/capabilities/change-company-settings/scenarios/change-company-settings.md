---
kind: primary
routes:
  web: Web
steps:
- text: The Admin adds, renames or removes sectors in Companies and saves
  kind: actor
  actor: admin
  entities:
  - entity: configuration
    effect: reads
    facts:
    - Company sectors
  contexts:
    web:
      place: crm-web::administration::settings
- text: The Product saves the sectors
  kind: product
  actor: admin
  entities:
  - entity: configuration
    effect: changes
    facts:
    - Company sectors
  contexts:
    web:
      place: crm-web::administration::settings
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/settings/SettingsPage.tsx#SettingsPage
---

# Change company sectors

## Trigger

The team's market segments change.

## Outcome

Company forms and filters offer the new sectors.
