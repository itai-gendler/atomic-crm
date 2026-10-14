---
appliesTo:
- type: entity
  id: tag
  effect: changes
permits:
- actors:
  - admin
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/settings/SettingsTags.tsx#SettingsTags
---

# Only an Admin edits a tag

Renaming or recolouring a tag happens in the settings. Any user creates tags while tagging contacts.
