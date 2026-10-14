---
kind: edge
routes:
  cli: Command line
steps:
- text: The Owner runs the build
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: A plugin that is on runs a build hook that fails or takes longer than it may
  kind: condition
  actor: owner
  entities:
  - {entity: plugin, effect: reads, facts: [Build hooks]}
  contexts:
    cli:
      place: cli
- text: The Product stops the build and names the plugin
  kind: product
  actor: owner
  entities:
  - {entity: plugin, effect: reads, facts: []}
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/plugin/wasm.go
---

# Build with a plugin whose hook fails

## Trigger

The Owner runs kite build on a site with a plugin that brings WebAssembly.

## Outcome

No site is written; a preview of the same page would have failed the same way.
