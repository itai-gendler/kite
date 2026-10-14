---
kind: primary
routes:
  cli: Command line
steps:
- text: The Owner names the kind and the title
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Product creates the post published, its publish time now, and prints where it wrote it
  kind: product
  actor: owner
  entities:
  - {entity: post, effect: creates, to: Published, facts: [Id, Title, Slug, Text, Publish time]}
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/commands.go#newNewCmd
---

# Create an item from the command line

## Trigger

The Owner runs kite new post "Hello".

## Outcome

A published post exists with an empty body, ready to be written in an editor of the Owner's choice.

## Edge cases

- A kind the site does not have is refused.
