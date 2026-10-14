---
appliesTo:
- type: capability
  id: merge-contacts
- type: entity
  id: contact
  facts:
  - Email addresses
  - Phone numbers
  - Tags
references:
- kind: code
  role: implementation
  target: supabase/functions/merge_contacts/index.ts
- kind: doc
  role: intent
  target: doc/src/content/docs/users/merging-contacts.mdx
---

# A merge keeps the target contact's values and adds the duplicate's

Where both contacts have a value the kept contact's wins; empty values are filled from the duplicate; emails, phone numbers and tags are combined without repeats; the latest last activity is kept; notes, tasks and deals move to the kept contact and the duplicate is deleted.
