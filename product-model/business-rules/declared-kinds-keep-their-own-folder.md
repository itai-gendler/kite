---
appliesTo:
- type: entity
  id: content-type
references:
- kind: code
  role: implementation
  target: internal/content/contenttype.go#Declare
---

# A declared kind keeps its items in a folder of its own and shares its name with nothing else

A kind is named by lowercase letters, digits, - and _, keeps its items in one folder directly under content/, which is also its listing's address, and cannot share its name or folder with another kind or a taxonomy. A declaration that breaks this changes nothing.
