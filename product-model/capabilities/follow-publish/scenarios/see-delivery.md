---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner opens the Deploy screen
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::deploy
- text: The Product shows each stage — saved, committed, pushed, deployed — with the uncommitted paths
    and the commits still to push
  kind: product
  actor: owner
  entities:
  - {entity: commit, effect: reads, facts: [Paths, Branch, Remote, Host, Live address]}
  contexts:
    studio:
      place: studio::signed-in::deploy
references:
- kind: code
  role: implementation
  target: internal/publish/git/publisher.go#State
---

# See how far a publish has got

## Trigger

The Owner wants to know whether what they published is live.

## Outcome

The Owner sees where the content has got and what is left to do.

## Edge cases

- A project that is not a Git repository shows the export only, and how to put the site in a repository.
