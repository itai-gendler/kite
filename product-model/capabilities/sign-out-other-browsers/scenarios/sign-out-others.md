---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner chooses Sign out other browsers
  kind: actor
  actor: owner
  entities:
  - {entity: session, as: this, effect: reads, facts: [Expires]}
  contexts:
    studio:
      place: studio::signed-in::account
- text: The Product ends every other session and renews this one
  kind: product
  actor: owner
  entities:
  - {entity: session, as: others, effect: removes}
  - {entity: session, as: this, effect: changes, facts: [Expires]}
  contexts:
    studio:
      place: studio::signed-in::account
references:
- kind: code
  role: implementation
  target: internal/api/account.go#handleEndSessions
---

# Sign out other browsers

## Trigger

The Owner signed in somewhere they should not stay signed in.

## Outcome

Every other browser has to sign in again.

## Edge cases

- For an account from the environment, other browsers are signed out by changing its password there.
