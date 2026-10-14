---
appliesTo:
- type: capability
  id: change-deal-settings
- type: entity
  id: configuration
  facts:
  - Deal stages
  - Deal categories
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/settings/SettingsPage.tsx#validateItemsInUse
- kind: doc
  role: intent
  target: doc/src/content/docs/users/settings.mdx
---

# A deal stage or category in use stays configured

The settings refuse to drop a stage or category any deal still has, and renaming one keeps its deals in it.
