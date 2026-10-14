---
kind: validation
routes:
  cli: Command line
steps:
- text: The Owner names a folder inside the Hexo site, or one that holds things and is not a Kite project
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Product refuses and changes nothing
  kind: product
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/import_cmd.go#newImportHexoCmd
---

# Import into a folder that cannot take it

## Trigger

The destination is wrong.

## Outcome

Neither folder is changed.
