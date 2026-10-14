---
kind: primary
routes:
  cli: Command line
steps:
- text: The Owner asks the command line to remove paper
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Product deletes the theme's folder
  kind: product
  actor: owner
  entities:
  - {entity: theme, effect: removes}
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/theme_cmd.go#newThemeRemoveCmd
---

# Remove a theme from the command line

## Trigger

The Owner runs kite theme remove paper.

## Outcome

The theme is gone.
