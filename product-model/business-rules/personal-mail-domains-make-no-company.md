---
appliesTo:
- type: capability
  id: capture-inbound-email
  contexts:
  - place: inbound-email
references:
- kind: code
  role: implementation
  target: supabase/functions/postmark/mailProvider.const.ts
- kind: code
  role: implementation
  target: supabase/functions/postmark/addNoteToContact.ts
---

# Personal mail domains never become companies

A contact created from an email at a personal mail provider gets no company.
