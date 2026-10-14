---
id: kite
summary: 'An open-source publishing platform: Markdown files edited in a browser studio, published as
  static pages, a live site, or a Git commit and push.'
category: publishing-platform
tags:
- markdown
- cms
- static-site-generator
- git
- blogging
authors:
- name: Kite contributors
  url: https://github.com/kite-plus/kite
license: Apache-2.0
languages:
- en
- zh-CN
limitations:
- Markdown files on disk are the source of truth; the index under .kite/ is a cache rebuilt from them.
- The studio has a single account, its owner; there are no other roles, authors or reader accounts.
- 'Publishing goes through Git: Kite commits and pushes, and whatever builds the repository deploys the
  site.'
- A push is never forced, and a remote's commits are never merged on the owner's behalf.
- Kite terminates no TLS of its own; a studio reachable from other machines sits behind something that
  does.
references:
- kind: doc
  role: intent
  target: README.md
- kind: doc
  role: intent
  target: docs/reference.md
- kind: doc
  role: context
  target: docs/design/architecture.md
- kind: code
  role: context
  target: cmd/kite/main.go
---

# Kite

Kite is a single program that holds a site's content as Markdown files on disk
and offers three ways to work with it: a studio in the browser where the owner
writes posts and pages, manages tags and categories, themes and plugins, and
publishes; a command line that builds, publishes, installs and connects; and a
server that renders the site itself. The same files become static pages
(`kite build`, or a zip exported from the studio), a live site (`kite serve`,
`kite run`, the container), or a Git commit that the repository's host builds
and deploys (`kite publish`, or Publish in the studio). Themes and plugins are
installed by name from a signed index and kept with the site.

## Intent

Write in Markdown, manage content in the browser, and publish on the owner's
terms: the writing experience of a CMS with the portability of a static site
generator. Files stay the owner's — saving rewrites only what changed, so
editing a title is a one-line diff — and where content lives and how it is
delivered are separate choices the owner can change their mind about.
