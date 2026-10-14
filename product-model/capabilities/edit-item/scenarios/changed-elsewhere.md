---
kind: edge
routes:
  studio: Studio
steps:
- text: The Owner saves a post
  kind: actor
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The post changed on disk since the editor loaded it
  kind: condition
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product refuses the save, overwrites nothing and answers with what is on disk now
  kind: product
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: [Title, Slug, Text, Publish time, Aliases]}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The editor shows part by part how it was when opened, the Owner's version and the stored one,
    and offers Merge both when they changed different parts
  kind: condition
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/api/write.go#failConflict
- kind: code
  role: implementation
  target: web/src/components/editor/ConflictDialog.tsx
---

# Save an item that changed elsewhere

## Trigger

Something else saved the item — another browser, an editor, git — while the Owner was writing.

## Outcome

Nothing was overwritten. The Owner keeps editing, discards theirs and loads the stored version, overwrites with theirs, or merges both and looks the result over before saving.
