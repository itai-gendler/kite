---
kind: validation
routes:
  cli: Command line
steps:
- text: The Owner runs kite ping for a site with no address
  kind: actor
  actor: owner
  entities:
  - {entity: site-settings, effect: reads, facts: [Address]}
  contexts:
    cli:
      place: cli
- text: The Product refuses, as a ping names the site by its address
  kind: product
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/ping_cmd.go#newPingCmd
---

# Ping a site with no address

## Trigger

site.baseURL is empty and KITE_SITE_BASEURL is not set.

## Outcome

Nothing is sent.
