---
kind: primary
routes:
  cli: Command line
steps:
- text: The Owner asks the command line to use vane
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Product sets the site's theme
  kind: product
  actor: owner
  entities:
  - {entity: site-settings, effect: changes, facts: [Theme in use]}
  - {entity: theme, effect: reads, facts: []}
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/theme_cmd.go#newThemeUseCmd
---

# Use a theme from the command line

## Trigger

The Owner runs kite theme use vane.

## Outcome

kite.yaml names the theme.
