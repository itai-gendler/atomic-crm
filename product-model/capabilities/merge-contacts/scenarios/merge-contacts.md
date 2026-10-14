---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Merge with another contact on a contact's page
  kind: actor
  actor: user
  entities:
  - entity: contact
    effect: reads
    as: duplicate
    facts:
    - First name
    - Last name
  contexts:
    web:
      place: crm-web::workspace::contact
- text: The Product proposes a contact with the same first and last name as the one to keep, and counts the notes, tasks and deals that will move
  kind: product
  actor: user
  entities:
  - entity: contact
    effect: reads
    as: kept
    facts:
    - First name
    - Last name
  - entity: contact-note
    effect: reads
    facts: []
  - entity: task
    effect: reads
    facts: []
  - entity: deal
    effect: reads
    facts:
    - Contacts
  contexts:
    web:
      place: crm-web::workspace::contact
- text: The User confirms Merge Contacts
  kind: actor
  actor: user
  entities:
  - entity: contact
    as: duplicate
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::contact
- text: The Product moves the duplicate's notes and tasks to the kept contact and puts the kept contact in its place on deals
  kind: product
  actor: user
  entities:
  - entity: contact-note
    effect: changes
    facts: []
  - entity: task
    effect: changes
    facts:
    - Contact
  - entity: deal
    effect: changes
    facts:
    - Contacts
  - entity: contact
    as: duplicate
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::contact
- text: The Product fills the kept contact's empty details from the duplicate, merges emails, phones and tags, and deletes the duplicate
  kind: product
  actor: user
  entities:
  - entity: contact
    effect: changes
    as: kept
    facts:
    - Gender
    - Title
    - Company
    - Email addresses
    - Phone numbers
    - LinkedIn URL
    - Background
    - Has newsletter
    - Account manager
    - Avatar
    - Tags
    - First seen
    - Last seen
  - entity: contact
    effect: removes
    as: duplicate
  - entity: tag
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::contact
- text: The Product opens the kept contact's page
  kind: product
  actor: user
  entities:
  - entity: contact
    effect: reads
    as: kept
    facts:
    - First name
    - Last name
  contexts:
    web:
      place: crm-web::workspace::contact
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/contacts/ContactMergeButton.tsx#ContactMergeButton
- kind: code
  role: implementation
  target: supabase/functions/merge_contacts/index.ts
---

# Merge a duplicate into another contact

## Trigger

The same person was entered twice, by hand, by import or by a captured email.

## Outcome

One contact remains with everything both had.

## Edge cases

- Where both contacts have a value, the kept contact's value wins.
- Merging cannot be undone.
