---
singleton: true
relations:
- entity: file
  verb: keeps
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: internal/config/config.go
- kind: code
  role: implementation
  target: internal/api/settings.go#settable
- kind: code
  role: implementation
  target: internal/lock/lock.go
---

# Site settings

What the site says about itself and how it is built and published: kite.yaml at the project's root, and the Kite release kite.lock pins.

## Information kept

- **Title** — what the site is called
- **Description** — shown in search results and feeds
- **Address** — the full address the site is published at (site.baseURL); every absolute link, the feed and the sitemap start with it
- **Language** — the language the site is written in
- **Author** — the owner's name, which the site credits as the author of what is published
- **Keywords** — written into every page for search engines
- **Time zone** — which day a date falls on
- **Search engine visibility** — whether every page asks search engines to leave it out (site.noindex)
- **Code at the end of the head** — added as written before </head> on every page
- **Code at the end of the page** — added as written before </body> on every page
- **Default category** — the category a post written in the studio starts in; Uncategorized in the site's language when left out, none when empty
- **Posts per page** — how many items a page of a listing shows, unless the theme says otherwise for that kind of listing
- **Posts in the feed** — how many of the newest posts the RSS feed carries
- **Theme in use** — the theme the site is built with; default is the built-in one
- **Theme settings** — the values of the settings themes declare; a value back at its default is not kept
- **Menus** — the links themes draw, by menu, kept apart from any theme
- **Publisher** — git, or none for a site whose owner commits and pushes by hand
- **Update services** — the services kite ping tells after each deploy (publish.ping)
- **Build stamp** — whether a build writes kite-build.json, naming the commit it was built from (build.stamp)
- **Theme and plugin index** — the index themes and plugins are installed from, and the key it is signed with; Kite's own unless set
- **Pinned Kite release** — the Kite release kite.lock pins, which kitew runs and the deploy builds with
- **Pinned release checksums** — the checksums of that release's archives kite.lock records
