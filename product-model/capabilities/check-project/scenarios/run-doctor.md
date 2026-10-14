---
kind: primary
routes:
  cli: Command line
steps:
- text: The Owner runs the check
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Product reports unreadable content, items with no id, themes and plugins changed by hand,
    and a pin that does not match
  kind: product
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: [Id]}
  - {entity: page, effect: reads, facts: [Id]}
  - {entity: theme, effect: reads, facts: [Changed by hand]}
  - {entity: plugin, effect: reads, facts: [Changed by hand]}
  - {entity: site-settings, effect: reads, facts: [Pinned Kite release]}
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/commands.go#printDoctor
---

# Check the project

## Trigger

The Owner runs kite doctor.

## Outcome

The Owner knows what needs fixing, or that no problems were found.
