---
kind: validation
routes:
  studio: Studio
steps:
- text: The Visitor enters a wrong user name or password
  kind: actor
  actor: visitor
  entities: []
  contexts:
    studio:
      place: studio::signed-out::sign-in
- text: The Product refuses with one message for either, so the form never tells whether an account exists
  kind: product
  actor: visitor
  entities:
  - {entity: account, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-out::sign-in
references:
- kind: code
  role: implementation
  target: internal/api/auth.go#handleLogin
---

# Sign in with a wrong name or password

## Trigger

The credentials are wrong.

## Outcome

The browser is not signed in.
