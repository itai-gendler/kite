---
kind: edge
routes:
  cli: Command line
steps:
- text: The Owner runs kite ping
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: One service does not answer in time or refuses
  kind: condition
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Product tries every other service, then fails the command
  kind: product
  actor: owner
  entities:
  - {entity: site-settings, effect: reads, facts: [Update services]}
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/ping_cmd.go#newPingCmd
---

# A service cannot be told

## Trigger

An update service is down.

## Outcome

The command fails; the workflow lets that job fail without failing the deployment.
