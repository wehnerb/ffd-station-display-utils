# ffd-station-display-utils

Shared utility functions for Fargo Fire Department station display Cloudflare Workers.

## What this is

This repository is the single source of truth for utility code that is used across
multiple station display Workers. Changes made here propagate automatically to all
Worker repositories via GitHub Actions.

## How it works

1. Edit a file in `utils/` in this repo
2. Bump the version number in `VERSION`
3. Add a line to `CHANGELOG.md` describing the change
4. Commit and push to `staging`
5. The `notify-workers.yml` workflow fires a `repository_dispatch` event to all
   eight Worker repos
6. Each Worker repo's `sync-utils.yml` workflow opens a PR against its own
   `staging` branch containing the updated utils files
7. Review each PR, test on staging, merge when ready

## What is shared

| File | Contents | Used by |
|------|----------|---------|
| `utils/constants.js` | Shared display constants (DARK_BG_COLOR etc.) | All workers |
| `utils/fetch-helpers.js` | fetchWithTimeout | All content workers |
| `utils/html.js` | escapeHtml, sanitizeParam | All content workers |
| `utils/google-auth.js` | getAccessToken, base64url, arrayBufferToBase64url | 4 workers |
| `utils/rotation.js` | getTodayString, getBlockIndex, getDaysElapsed, getSecondsUntilNextRotation | 2 workers |

## What is NOT shared

Worker-specific config (layouts, cache versions, rotation anchors), page renderers,
ICS parser, and any code used by only one worker stays in that worker's own repo.

## Versioning

- **Patch (1.0.x):** Bug fix, behavior unchanged for callers
- **Minor (1.x.0):** New function added, old callers unaffected
- **Major (x.0.0):** Breaking change — update callers before merging sync PRs

## Never do this

Do not edit files inside any Worker's `src/shared/` directory directly.
They are overwritten on every sync. Edit the source here instead.
