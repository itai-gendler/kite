---
kind: alternative
routes:
  site: Site
steps:
- text: The Reader opens the listing of a declared kind, such as /projects/
  kind: actor
  actor: reader
  entities: []
  contexts:
    site:
      place: site
- text: 'The Product lists its public items in the order the kind says: by weight, smallest first, or
    by date, newest first'
  kind: product
  actor: reader
  entities:
  - {entity: content-type, effect: reads, facts: [Folder, Order]}
  - {entity: declared-content, effect: reads, facts: [Title, Weight, Fields, Publish time]}
  contexts:
    site:
      place: site
references:
- kind: code
  role: implementation
  target: internal/content/contenttype.go#Type
---

# Read the listing of a declared kind

## Trigger

A reader browses a portfolio.

## Outcome

The reader sees the items in their order; Previous and Next follow it.
