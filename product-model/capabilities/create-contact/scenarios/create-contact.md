---
kind: primary
routes:
  web: Web
steps:
- text: The User enters the contact's name, title, company, email addresses, phone numbers, background and account manager
  kind: actor
  actor: user
  entities:
  - entity: company
    effect: reads
    facts: []
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::new-contact
- text: The Product creates the contact, seen now, without tags and managed by the chosen user
  kind: product
  actor: user
  entities:
  - entity: contact
    effect: creates
    facts:
    - First name
    - Last name
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
    - First seen
    - Last seen
    - Tags
  - entity: tag
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::new-contact
- text: The Product opens the new contact's page
  kind: product
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts:
    - First name
    - Last name
  contexts:
    web:
      place: crm-web::workspace::contact
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/contacts/ContactCreate.tsx#ContactCreate
- kind: code
  role: implementation
  target: src/components/atomic-crm/contacts/contactModel.ts#cleanupContactForCreate
- kind: code
  role: implementation
  target: supabase/schemas/02_functions.sql#handle_contact_saved
---

# Create a contact

## Trigger

A User meets someone new.

## Outcome

The contact exists and the User is on its page.

## Edge cases

- Typing an email first fills an empty first and last name from the address.
- Only active users are offered as account manager.
