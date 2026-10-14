---
appliesTo:
- type: entity
  id: tag
  effect: removes
permits:
- actors:
  - admin
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/settings/SettingsTags.tsx#SettingsTags
---

# Only an Admin deletes a tag

Deleting a tag happens in the settings.
