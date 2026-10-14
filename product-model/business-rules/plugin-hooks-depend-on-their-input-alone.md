---
appliesTo:
- type: capability
  id: build-site
- type: capability
  id: preview-item
references:
- kind: code
  role: implementation
  target: internal/plugin/wasm.go
- kind: doc
  role: intent
  target: docs/reference.md
  title: Build hooks
---

# A plugin's build hooks answer from what they are handed alone

A hook reaches no network and no files, its clock and random numbers are fixed, and it has bounded memory and time; one that fails or takes longer fails the build and is named, and a preview runs the same hooks.

## Rationale

What a build publishes has to be the same on every machine.
