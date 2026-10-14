---
kind: edge
routes:
  studio: Studio
steps:
- text: The Owner chooses Publish in the editor
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::editor
- text: A pre-commit, prepare-commit-msg or commit-msg hook of the repository refuses to let it be made
  kind: condition
  actor: owner
  entities:
  - {entity: commit, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product leaves the repository exactly as it found it and shows what the hook said
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Owner chooses Publish without the hooks
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product commits without running the hooks and pushes
  kind: product
  actor: owner
  entities:
  - {entity: commit, effect: creates, to: Committed, facts: [Message, Paths, Branch, Hash]}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The push reaches the remote
  kind: product
  actor: owner
  entities:
  - {entity: commit, effect: changes, from: Committed, to: Pushed, facts: [Remote]}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/publish/git/publisher.go#commit
- kind: code
  role: implementation
  target: web/src/components/publish/Delivery.tsx
---

# Publish after a commit hook refuses

## Trigger

The repository's owner set hooks that object to the commit.

## Outcome

The publish went through only after the Owner read the refusal and chose to skip the hooks.
