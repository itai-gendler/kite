---
kind: alternative
routes:
  studio: Studio
steps:
- text: A commit was pushed to a public repository on GitHub whose host — GitHub's own, Vercel or Cloudflare
    — records deployments
  kind: condition
  unattended: true
  entities:
  - {entity: commit, effect: reads, facts: [Remote]}
  contexts:
    studio:
      place: studio::signed-in::deploy
- text: The Product asks GitHub's API, read-only, what the host recorded for the commit
  kind: product
  entities:
  - {entity: commit, effect: changes, from: Pushed, to: Deploying, facts: [Host]}
  contexts:
    studio:
      place: studio::signed-in::deploy
- text: The host records the deployment as finished
  kind: condition
  entities: []
  contexts:
    studio:
      place: studio::signed-in::deploy
- text: The Product marks the commit live where the host says
  kind: product
  entities:
  - {entity: commit, effect: changes, from: Deploying, to: Live, facts: [Live address]}
  contexts:
    studio:
      place: studio::signed-in::deploy
references:
- kind: code
  role: implementation
  target: internal/publish/git/deploy.go#newDeployChecker
- kind: code
  role: implementation
  target: internal/publish/git/deploy.go#hostOf
---

# The host reports the deployment

## Trigger

The repository is on GitHub and its host records deployments.

## Outcome

The panel showed the deployment under way, then live.

## Edge cases

- Anonymous questions share GitHub's sixty an hour: the studio asks at most once a minute, every five once a deployment has taken ten, and says when it will ask again when the allowance is nearly spent.
- A repository connected with a token is asked with it, which reaches a private repository.
