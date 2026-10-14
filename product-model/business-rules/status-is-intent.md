---
appliesTo:
- type: capability
  id: publish-items
- type: capability
  id: change-item-status
references:
- kind: code
  role: implementation
  target: internal/publish/publish.go#DeliveryState
- kind: code
  role: implementation
  target: web/src/components/editor/EditorPage.tsx#EditorPage
- kind: code
  role: implementation
  target: internal/content/content.go#Status
---

# Publishing an item never changes its status

An item's status — Draft, Published, Scheduled, Archived — is the owner's intent for the site, set in the status menu and saved with the item. Publishing commits and pushes the item's files as they are: a draft that is published is committed and pushed, and stays a draft that is not on the site.

## Rationale

How far content has travelled — committed, pushed, deployed — is kept apart from whether the owner means it to be public, so that "published" does not mean two things on one screen.
