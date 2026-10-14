---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner changes their name and email and chooses Save profile
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::account
- text: The Product writes the name as the site's author in kite.yaml and keeps the email on the server
  kind: product
  actor: owner
  entities:
  - {entity: site-settings, effect: changes, facts: [Author]}
  - {entity: account, effect: changes, facts: [Email]}
  contexts:
    studio:
      place: studio::signed-in::account
references:
- kind: code
  role: implementation
  target: web/src/features/settings/account/index.tsx
---

# Save the profile

## Trigger

The Owner wants the site to credit them differently.

## Outcome

The studio calls the Owner by the new name; the site credits it once kite.yaml is published. The email is never published.
