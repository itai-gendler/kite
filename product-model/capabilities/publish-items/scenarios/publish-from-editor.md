---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner chooses Publish in the editor of a post with unsaved changes
  kind: actor
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product saves the post first
  kind: product
  actor: owner
  entities:
  - {entity: post, effect: changes, facts: [Text, Last saved]}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: 'The Product looks the repository over and commits exactly the post''s folder, as "publish: <title>"'
  kind: product
  actor: owner
  entities:
  - {entity: commit, effect: creates, to: Committed, facts: [Message, Paths, Branch, Hash]}
  - {entity: post, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product pushes the commit to the remote
  kind: product
  actor: owner
  entities:
  - {entity: commit, effect: changes, from: Committed, to: Pushed, facts: [Remote]}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The post keeps the status it had
  kind: condition
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/api/publish.go#publishRequest
- kind: code
  role: implementation
  target: internal/publish/git/publisher.go#commit
- kind: code
  role: implementation
  target: web/src/components/editor/EditorPage.tsx#EditorPage
---

# Publish an item from the editor

## Trigger

The Owner wants what they wrote to reach the deployed site.

## Outcome

The commit is on the remote and the publishing panel follows it toward the site. The post's status is what it was: a draft published this way is committed and pushed, and is still not on the site.

## Edge cases

- Everything else in the working tree stays as it was: what the Owner staged stays staged, and other changes stay uncommitted.
- Asking to publish an item that is already committed changes nothing and says there is nothing to publish.
