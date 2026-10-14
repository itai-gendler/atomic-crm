---
kind: edge
routes:
  web: Web
steps:
- text: The Visitor opens the set-password page without a valid link
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: crm-web::sign-in::set-password
- text: The Product explains that the link is missing its tokens and offers no form
  kind: product
  actor: visitor
  entities: []
  contexts:
    web:
      place: crm-web::sign-in::set-password
references:
- kind: code
  role: implementation
  target: src/components/supabase/set-password-page.tsx#SetPasswordPage
---

# A link without its tokens is refused

## Trigger

A Visitor reaches the set-password page by a broken or copied address.

## Outcome

No password is set.
