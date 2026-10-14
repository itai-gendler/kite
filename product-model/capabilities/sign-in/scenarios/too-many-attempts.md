---
kind: edge
routes:
  studio: Studio
steps:
- text: The Visitor tries again after several failed attempts
  kind: actor
  actor: visitor
  entities: []
  contexts:
    studio:
      place: studio::signed-out::sign-in
- text: The Product refuses for now and says how long to wait
  kind: product
  actor: visitor
  entities: []
  contexts:
    studio:
      place: studio::signed-out::sign-in
references:
- kind: code
  role: implementation
  target: internal/auth/throttle.go
---

# Sign in after too many failures

## Trigger

Sign-in attempts keep failing.

## Outcome

No attempt is checked until the wait is over.

## Edge cases

- There is no reset email: a forgotten password is set again on the server, with kite auth set-password or the environment.
