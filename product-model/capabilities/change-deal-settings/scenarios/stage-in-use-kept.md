---
kind: validation
routes:
  web: Web
steps:
- text: The Admin removes a stage or category and saves
  kind: actor
  actor: admin
  entities:
  - entity: configuration
    effect: reads
    facts:
    - Deal stages
    - Deal categories
  contexts:
    web:
      place: crm-web::administration::settings
- text: Some deals are still in that stage or category
  kind: condition
  entities:
  - entity: deal
    effect: reads
    facts:
    - Stage
    - Category
  contexts:
    web:
      place: crm-web::administration::settings
- text: The Product names the values still used by deals and saves nothing
  kind: product
  actor: admin
  entities:
  - entity: deal
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::administration::settings
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/settings/SettingsPage.tsx#validateItemsInUse
---

# A stage or category still used by deals cannot be removed

## Trigger

An Admin prunes the pipeline while deals still use a value.

## Outcome

The settings are unchanged.

## Edge cases

- Two stages or two categories with the same name are refused the same way.
