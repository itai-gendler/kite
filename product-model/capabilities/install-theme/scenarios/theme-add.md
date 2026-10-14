---
kind: primary
routes:
  cli: Command line
steps:
- text: The Owner asks the command line to add vane by name
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Product installs the newest version of vane the index lists that works with this Kite, checks
    it and records it in kite.lock
  kind: product
  actor: owner
  entities:
  - {entity: theme, effect: creates, facts: [Name, Version, Author, Settings it declares, Page templates,
      Menus it draws, Loads from, Installed from the index]}
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/theme_cmd.go#newThemeAddCmd
---

# Install a theme from the command line

## Trigger

The Owner runs kite theme add vane.

## Outcome

The theme is in themes/.

## Edge cases

- A name that is a file or a folder installs that archive or folder instead; --replace replaces a theme of the same name.
