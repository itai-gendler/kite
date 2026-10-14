---
kind: edge
routes:
  studio: Studio
steps:
- text: The host is deploying a pushed commit
  kind: condition
  unattended: true
  entities:
  - {entity: commit, effect: reads, facts: [Host]}
  contexts:
    studio:
      place: studio::signed-in::deploy
- text: The host records that the deployment failed
  kind: condition
  entities: []
  contexts:
    studio:
      place: studio::signed-in::deploy
- text: The Product marks the commit as failed to deploy
  kind: product
  entities:
  - {entity: commit, effect: changes, from: Deploying, to: Deploy failed, facts: []}
  contexts:
    studio:
      place: studio::signed-in::deploy
references:
- kind: code
  role: implementation
  target: internal/publish/git/deploy.go#status
---

# The host reports a failed deployment

## Trigger

The deployment broke on the host.

## Outcome

The panel says the host reports a failure; only the host can say so — the site itself cannot tell a failed deployment from a slow one.
