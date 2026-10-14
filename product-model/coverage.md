---
scope: The studio and its HTTP API, the command line, the Git publisher and the site Kite serves.
method: Static reading of source, design documents and the reference guide at the pinned commit; nothing
  was run.
covered:
- description: The HTTP API, modeled as the studio's own contract
  paths:
  - internal/api/
- description: The studio front end
  paths:
  - web/src/
- description: The Git publisher, GitHub connection, deployment checks and update pings
  paths:
  - internal/publish/
- description: The content model, declared content types, the file store and front matter editing
  paths:
  - internal/content/
  - internal/store/
  - internal/frontmatter/
- description: The server runtime that serves the site and the studio
  paths:
  - internal/serve/
- description: The account, its profile, sessions and first-run setup
  paths:
  - internal/auth/
  - internal/setup/
- description: The index of themes and plugins, install records and archives
  paths:
  - internal/apps/
  - internal/lock/
  - internal/archive/
- description: The pinned Kite release, kitew and the deploy workflows, and the build stamp
  paths:
  - internal/kitew/
  - internal/stamp/
- description: Opening a site, its configuration, build output and index
  paths:
  - internal/site/
  - internal/config/
  - internal/project/
  - internal/index/
  - internal/build/
- description: What plugins put on pages and run while the site is built, as readers and builds meet it
  paths:
  - internal/plugin/
- description: Importing a Hexo site
  paths:
  - internal/importer/
- description: The commands for serving, building, publishing, GitHub, themes, plugins, the index, the
    account, the wrapper, pinging, creating a site or an item, importing and checking the project
  paths:
  - internal/cli/serve_cmd.go
  - internal/cli/build_cmd.go
  - internal/cli/publish_cmd.go
  - internal/cli/github_cmd.go
  - internal/cli/theme_cmd.go
  - internal/cli/plugin_cmd.go
  - internal/cli/apps_cmd.go
  - internal/cli/auth_cmd.go
  - internal/cli/wrapper_cmd.go
  - internal/cli/ping_cmd.go
  - internal/cli/init_cmd.go
  - internal/cli/first_run.go
  - internal/cli/import_cmd.go
  - internal/cli/commands.go
exclusions:
- description: 'Build, release, container and CI tooling: how Kite itself is built and shipped'
  paths:
  - .github/
  - docker/
  - Dockerfile
  - docker-compose.yaml
  - Makefile
  - .goreleaser.yaml
  - scripts/
  - .golangci.yml
- description: 'Browser end-to-end tests and the performance harness: development tooling'
  paths:
  - web/e2e/
  - internal/perf/
- description: 'Documentation images and the studio''s static icons: assets, no behavior'
  paths:
  - docs/assets/
  - web/public/
unmapped:
- description: 'The theme contract kite/v1 and rendering vocabulary (template functions, shortcodes, image
    processing, pagination objects): a developer interface for theme authors, documented in theme-system.md;
    what readers see of it is mapped'
  paths:
  - internal/render/
  - internal/reader/
  - internal/schema/
  - internal/hook/
  - themes/
- description: 'Theme and plugin authoring commands (new, verify, pack): tools for theme and plugin developers,
    not the owner''s use of a site'
  paths:
  - internal/cli/pack_cmd.go
  - internal/pack/
  - internal/themecheck/
- description: 'The studio''s own display preferences (colors, sidebar, layout): kept per browser, never
    with the site'
  paths:
  - web/src/features/settings/appearance/
  - web/src/components/config-drawer.tsx
- description: 'Index-cache maintenance and diagnostics (kite index, kite list, kite version, kite openapi):
    plumbing over the derived cache and the API description'
  paths:
  - internal/cli/index_cmd.go
  - internal/cli/openapi_cmd.go
limitations:
- description: What GitHub, Vercel and Cloudflare Pages record for a deployment, and how the deployment
    checks read it
  paths:
  - internal/publish/git/deploy.go
---

# Coverage
