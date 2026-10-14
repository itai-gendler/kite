---
kind: alternative
routes:
  cli: Command line
steps:
- text: The Owner runs kite build --verify
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Product builds the site twice at one instant and compares every byte
  kind: product
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: [Text]}
  - {entity: site-settings, effect: reads, facts: [Theme in use]}
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/build_cmd.go#verifyBuild
---

# Verify that a build is reproducible

## Trigger

The deploy workflow checks the site would deploy the same on a second run.

## Outcome

The command fails, naming the files that differ, when two builds disagree.
