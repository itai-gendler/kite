---
appliesTo:
- type: capability
  id: edit-item
- type: capability
  id: change-item-status
references:
- kind: code
  role: implementation
  target: web/src/hooks/useItem.ts#autosaves
---

# Only a draft saves itself

A draft saves shortly after the owner stops typing, as no reader sees it. A published, scheduled or archived item saves only when the owner chooses Save, because saving it changes the site; until then what was typed is kept in the browser.
