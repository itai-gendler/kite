---
kind: alternative
routes:
  cli: Command line
steps:
- text: The Owner runs the check with --fix-ids in a site moved from Hugo
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Product writes a new id into every post and page that has none, changing nothing else in them
  kind: product
  actor: owner
  entities:
  - {entity: post, effect: changes, facts: [Id]}
  - {entity: page, effect: changes, facts: [Id]}
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/commands.go#newDoctorCmd
---

# Give every item an id

## Trigger

The Owner runs kite doctor --fix-ids.

## Outcome

Every item has the id Kite keeps it by.

## Edge cases

- Two files carrying the same id stop the check; which copy keeps the identity is left to the Owner.
