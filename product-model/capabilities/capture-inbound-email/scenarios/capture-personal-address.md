---
kind: primary
routes:
  email: Inbound email
steps:
- text: The Inbound email service posts an email sent to an address at a personal mail provider
  kind: actor
  actor: inbound-email-service
  entities: []
  contexts:
    email:
      place: inbound-email
- text: The Product creates the recipient's contact without a company
  kind: product
  entities:
  - entity: contact
    effect: creates
    facts:
    - First name
    - Last name
    - Email addresses
    - Account manager
    - First seen
    - Last seen
    - Tags
  - entity: company
    effect: reads
    facts: []
  contexts:
    email:
      place: inbound-email
- text: The Product adds the email as a note on the new contact
  kind: product
  entities:
  - entity: contact-note
    effect: creates
    facts:
    - Text
    - Date
    - Attachments
    - Author
  - entity: contact
    effect: reads
    facts: []
  contexts:
    email:
      place: inbound-email
references:
- kind: code
  role: implementation
  target: supabase/functions/postmark/addNoteToContact.ts
- kind: code
  role: implementation
  target: supabase/functions/postmark/mailProvider.const.ts
---

# A personal email address gets no company

## Trigger

A user writes to someone's personal address.

## Outcome

The contact exists with no company.
