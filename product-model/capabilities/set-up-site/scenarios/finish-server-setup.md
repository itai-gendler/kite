---
kind: primary
routes:
  studio: Studio
steps:
- text: The Visitor opens the address the server printed and gives the site's name, address and language
    and their own name
  kind: actor
  actor: visitor
  entities: []
  contexts:
    studio:
      place: studio::signed-out::setup
- text: The Visitor chooses a user name and a password of at least 8 characters, twice, and chooses Finish
  kind: actor
  actor: visitor
  entities: []
  contexts:
    studio:
      place: studio::signed-out::setup
- text: The Product writes the site's description to kite.yaml first
  kind: product
  actor: visitor
  entities:
  - {entity: site-settings, effect: changes, facts: [Title, Address, Language, Author]}
  contexts:
    studio:
      place: studio::signed-out::setup
- text: The Product stores the account, which ends the setup, and signs this browser in
  kind: product
  actor: visitor
  entities:
  - {entity: account, effect: creates, facts: [User name, Password, Comes from]}
  - {entity: session, effect: creates, facts: [Expires, Remembered], with: account}
  - {entity: studio-server, effect: changes, facts: [Waiting for setup]}
  contexts:
    studio:
      place: studio::signed-out::setup
references:
- kind: code
  role: implementation
  target: internal/api/setup.go#handleSetup
---

# Finish setting up a server

## Trigger

A server reachable from other machines was started with the studio, changes allowed and no account — a fresh container, for instance.

## Outcome

The site is described, the account exists, and the browser is in the studio. From now on the studio asks for a sign-in.

## Edge cases

- A failure before the account is stored leaves the setup open and the form usable.
- A description left empty is not written.
