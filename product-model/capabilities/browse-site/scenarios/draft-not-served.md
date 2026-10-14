---
kind: edge
routes:
  site: Site
steps:
- text: The Reader opens the address a draft post would have
  kind: actor
  actor: reader
  entities:
  - {entity: post, effect: reads, facts: []}
  contexts:
    site:
      place: site
- text: The site is served without drafts
  kind: condition
  actor: reader
  entities:
  - {entity: post, effect: reads, facts: []}
  contexts:
    site:
      place: site
- text: The Product answers with the site's not-found answer
  kind: product
  actor: reader
  entities: []
  contexts:
    site:
      place: site
references:
- kind: code
  role: implementation
  target: internal/content/content.go#IsPublic
---

# Open the address of a draft

## Trigger

A reader guesses or keeps the address of an unpublished post.

## Outcome

Nothing of the draft is shown.
