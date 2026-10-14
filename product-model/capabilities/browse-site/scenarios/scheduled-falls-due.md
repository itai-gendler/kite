---
kind: alternative
routes:
  site: Site
steps:
- text: A scheduled post's publish time passes while the server runs
  kind: condition
  unattended: true
  entities:
  - {entity: post, effect: reads, facts: [Publish time]}
  contexts:
    site:
      place: site
- text: The Product re-plans the site so the post is served from then on
  kind: product
  entities:
  - {entity: post, effect: reads, facts: [Title, Slug]}
  contexts:
    site:
      place: site
references:
- kind: code
  role: implementation
  target: internal/serve/server.go#Reload
---

# A scheduled post falls due

## Trigger

The time of a scheduled post comes.

## Outcome

Readers of a site Kite serves see the post without anyone building again.
