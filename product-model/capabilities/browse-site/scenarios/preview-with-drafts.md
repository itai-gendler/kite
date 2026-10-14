---
kind: alternative
routes:
  site: Site
steps:
- text: The Reader opens a draft post on a site kite run serves
  kind: actor
  actor: reader
  entities:
  - {entity: post, effect: reads, facts: []}
  contexts:
    site:
      place: site
- text: The server includes drafts
  kind: condition
  actor: reader
  entities:
  - {entity: studio-server, effect: reads, facts: [Drafts included]}
  contexts:
    site:
      place: site
- text: The Product serves the draft as it would be published
  kind: product
  actor: reader
  entities:
  - {entity: post, effect: reads, facts: [Title, Text]}
  contexts:
    site:
      place: site
references:
- kind: code
  role: implementation
  target: internal/cli/serve_cmd.go#newRunCmd
---

# Read drafts on the local preview

## Trigger

The owner previews the whole site locally.

## Outcome

Drafts show beside published items; nothing about them is published.
