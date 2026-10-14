---
kind: validation
routes:
  cli: Command line
steps:
- text: The Owner runs kite build --output naming a folder that holds things a build did not write
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Product refuses and leaves the folder as it is
  kind: product
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/site/output.go
---

# Build into a folder that is not its own

## Trigger

The output named is a home folder, the project, or one of its own folders.

## Outcome

Nothing is replaced: a build replaces only a folder a build of this project wrote, or one holding this site's sitemap or feed.
