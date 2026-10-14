---
kind: primary
routes:
  email: Inbound email
steps:
- text: The Inbound email service posts an email a user sent with the inbound address in copy
  kind: actor
  actor: inbound-email-service
  entities:
  - entity: user
    effect: reads
    facts: []
  contexts:
    email:
      place: inbound-email
- text: The Product recognises the sender as an active user account by main or secondary email
  kind: product
  entities:
  - entity: user-account
    effect: reads
    facts:
    - Email
    - Secondary emails
  contexts:
    email:
      place: inbound-email
- text: The Product creates a company named after the email domain for each unknown recipient
  kind: product
  entities:
  - entity: company
    effect: creates
    facts:
    - Name
    - Website
    - Account manager
    - Added on
  contexts:
    email:
      place: inbound-email
- text: The Product finds each recipient's contact by email, or creates it at that company, managed by the sender
  kind: product
  entities:
  - entity: contact
    effect: creates
    facts:
    - First name
    - Last name
    - Email addresses
    - Company
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
- text: The Product adds the subject and body as a note on each recipient's contact, written by the sender, with the email's attachments, and marks the contact seen now
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
  target: supabase/functions/postmark/index.ts
- kind: code
  role: implementation
  target: supabase/functions/postmark/addNoteToContact.ts
- kind: code
  role: implementation
  target: supabase/functions/postmark/extractMailContactData.ts
- kind: doc
  role: intent
  target: doc/src/content/docs/users/inbound-email.mdx
---

# Capture an email sent to a contact

## Trigger

A user writes to a contact and puts the inbound address in Cc or Bcc.

## Outcome

The email is a note on the contact, which exists along with its company.

## Edge cases

- An existing company is reused when its website or name matches the email domain.
