---
availability:
- place: studio::signed-in
references:
- kind: code
  role: implementation
  target: web/src/components/editor/PublishMenu.tsx#PublishMenu
- kind: code
  role: implementation
  target: internal/content/content.go#IsPublic
- kind: code
  role: implementation
  target: internal/content/content.go#Validate
---

# Change an item's status

Set an item to Draft, Published, Scheduled or Archived, and its publish time, from the status menu beside Publish. The status is the owner's intent for the site; it takes effect when the item is saved, and says nothing about whether the item has been committed, pushed or deployed.
