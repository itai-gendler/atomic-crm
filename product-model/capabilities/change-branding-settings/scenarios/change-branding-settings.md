---
kind: primary
routes:
  web: Web
steps:
- text: The Admin changes the app title or a logo in Branding and saves
  kind: actor
  actor: admin
  entities:
  - entity: configuration
    effect: reads
    facts:
    - App title
    - Light mode logo
    - Dark mode logo
  contexts:
    web:
      place: crm-web::administration::settings
- text: The Product saves the settings and shows the new name and logos at once
  kind: product
  actor: admin
  entities:
  - entity: configuration
    effect: changes
    facts:
    - App title
    - Light mode logo
    - Dark mode logo
  contexts:
    web:
      place: crm-web::administration::settings
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/settings/SettingsPage.tsx#SettingsPage
---

# Change the name and logos

## Trigger

The team brands its CRM.

## Outcome

Every user sees the new name and logos.

## Edge cases

- Reset to Defaults fills the whole form with the shipped values, to be saved like any change.
