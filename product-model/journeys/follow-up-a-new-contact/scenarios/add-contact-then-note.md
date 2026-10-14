---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The User enters the new contact's details
  kind: actor
  capability: create-contact
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::new-contact
- text: The Product creates the contact
  kind: product
  capability: create-contact
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
  contexts:
    web:
      place: crm-web::workspace::new-contact
- text: The Product opens the new contact's page
  kind: product
  capability: create-contact
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
- text: The User writes a note with the contact's status and chooses Add this note
  kind: actor
  capability: add-note
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::contact
- text: The Product saves the note and gives the contact its status
  kind: product
  capability: add-note
  actor: user
  entities:
  - entity: contact-note
    effect: creates
    facts:
    - Text
    - Date
    - Status
    - Attachments
    - Author
  - entity: contact
    effect: changes
    facts:
    - Status
    - Last seen
  contexts:
    web:
      place: crm-web::workspace::contact
---

# Create a contact, then note the conversation

## Trigger

A User comes back from meeting someone new.

## Outcome

The contact exists and its first note records the conversation.
