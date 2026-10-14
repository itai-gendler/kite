---
kind: alternative
routes:
  cli: Command line
steps:
- text: The Owner names the kind and the title, with --draft
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Product creates the post as a draft
  kind: product
  actor: owner
  entities:
  - {entity: post, effect: creates, to: Draft, facts: [Id, Title, Slug, Text]}
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/commands.go#newNewCmd
---

# Create a draft from the command line

## Trigger

The Owner runs kite new post "Hello" --draft.

## Outcome

A draft post exists.
