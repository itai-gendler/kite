---
kind: alternative
routes:
  site: Site
steps:
- text: The Reader opens an address a post lists among its aliases
  kind: actor
  actor: reader
  entities:
  - {entity: post, effect: reads, facts: []}
  contexts:
    site:
      place: site
- text: The Product answers with a redirect that sends the browser on to the post at once and names its
    address for search engines
  kind: product
  actor: reader
  entities:
  - {entity: post, effect: reads, facts: [Aliases, Slug]}
  contexts:
    site:
      place: site
references:
- kind: code
  role: implementation
  target: internal/serve/router.go#spellings
---

# Follow an old address

## Trigger

A link to an address the post had before.

## Outcome

The reader reaches the post.
