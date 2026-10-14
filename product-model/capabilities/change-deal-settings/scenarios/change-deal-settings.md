---
kind: primary
routes:
  web: Web
steps:
- text: The Admin changes the currency, stages, pipeline statuses or categories in Deals and saves
  kind: actor
  actor: admin
  entities:
  - entity: configuration
    effect: reads
    facts:
    - Currency
    - Deal stages
    - Pipeline statuses
    - Deal categories
  - entity: deal
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::administration::settings
- text: The Product saves the settings; renamed stages and categories keep their deals
  kind: product
  actor: admin
  entities:
  - entity: configuration
    effect: changes
    facts:
    - Currency
    - Deal stages
    - Pipeline statuses
    - Deal categories
  - entity: deal
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

# Change the pipeline and categories

## Trigger

The team's sales process changes.

## Outcome

The board shows the new columns and deal forms offer the new values.
