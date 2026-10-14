---
kind: edge
routes:
  studio: Studio
steps:
- text: A commit was pushed, the host records no deployments and the site cannot be asked
  kind: condition
  unattended: true
  entities:
  - {entity: commit, effect: reads, facts: [Remote]}
  contexts:
    studio:
      place: studio::signed-in::deploy
- text: The Product stops waiting and says the host does not report deployments, so the site itself is
    the answer
  kind: product
  entities:
  - {entity: commit, effect: reads, facts: [Hash]}
  contexts:
    studio:
      place: studio::signed-in::deploy
references:
- kind: code
  role: implementation
  target: internal/publish/git/publisher.go#combine
---

# Nobody can tell

## Trigger

Neither witness can say whether the commit is live.

## Outcome

The commit stays pushed; the panel says so rather than waiting.
