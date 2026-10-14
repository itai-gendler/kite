---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner changes the title and the text of a draft post
  kind: actor
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: [Title, Text]}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The post is a draft, so it saves without being asked
  kind: condition
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product saves the changes against the version the editor loaded, rewriting only what changed
  kind: product
  actor: owner
  entities:
  - {entity: post, effect: changes, facts: [Title, Text, Last saved]}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: web/src/hooks/useItem.ts#autosaves
- kind: code
  role: implementation
  target: internal/api/write.go#handleUpdate
---

# A draft saves itself

## Trigger

The Owner is writing a draft.

## Outcome

The draft is saved within seconds of typing stopping, and no later than fifteen seconds while typing goes on; the editor says when it was saved.

## Edge cases

- A save that cannot reach the server is tried again; meanwhile what was typed stays in the browser.
- A document using footnotes, raw HTML, HTML entities or shortcodes opens as Markdown, since the visual editor cannot keep them.
