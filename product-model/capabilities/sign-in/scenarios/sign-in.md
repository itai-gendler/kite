---
kind: primary
routes:
  studio: Studio
steps:
- text: The Visitor enters the user name and password, ticks Keep me signed in and chooses Sign in
  kind: actor
  actor: visitor
  entities: []
  contexts:
    studio:
      place: studio::signed-out::sign-in
- text: The Product checks them and signs the browser in
  kind: product
  actor: visitor
  entities:
  - {entity: account, effect: reads, facts: [User name, Password]}
  - {entity: session, effect: creates, facts: [Expires, Remembered]}
  contexts:
    studio:
      place: studio::signed-out::sign-in
references:
- kind: code
  role: implementation
  target: internal/api/auth.go#handleLogin
---

# Sign in

## Trigger

The owner opens the studio of a site with a password.

## Outcome

The browser is in the studio until the session expires.
