---
kind: alternative
routes:
  site: Site
steps:
- text: The Reader opens a post
  kind: actor
  actor: reader
  entities:
  - {entity: post, effect: reads, facts: [Title]}
  contexts:
    site:
      place: site
- text: A plugin that is on puts code on single posts, and the post does not turn it off in its front
    matter
  kind: condition
  actor: reader
  entities:
  - {entity: plugin, effect: reads, facts: [Adds code to pages, Settings]}
  - {entity: post, effect: reads, facts: []}
  contexts:
    site:
      place: site
- text: The Product serves the post with the plugin's code in the head or before the end of the body,
    filled with its settings
  kind: product
  actor: reader
  entities:
  - {entity: post, effect: reads, facts: [Text]}
  - {entity: plugin, effect: reads, facts: []}
  contexts:
    site:
      place: site
references:
- kind: code
  role: implementation
  target: internal/plugin/inject.go
- kind: doc
  role: intent
  target: docs/reference.md
  title: Plugins
---

# Read a page a plugin adds to

## Trigger

A comments or analytics plugin is on.

## Outcome

The reader's browser runs what the plugin adds, loading from the sites it names.
