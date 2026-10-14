---
kind: primary
routes:
  cli: Command line
steps:
- text: The Owner runs kite ping
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Product sends each listed service the site's title, its address and the address of its feed,
    giving each ten seconds to answer
  kind: product
  actor: owner
  entities:
  - {entity: site-settings, effect: reads, facts: [Title, Address, Update services]}
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/publish/ping/ping.go#Send
---

# Ping the update services

## Trigger

A deploy went live.

## Outcome

A line per service says what it answered.

## Edge cases

- A site without a feed sends the plain ping, without the feed's address.
