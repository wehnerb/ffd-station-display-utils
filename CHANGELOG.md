# Changelog

## - v0.7.0 - 2026-05-02

### Changed
- TEXT_TERTIARY opacity bumped from 0.38 to 0.50 for improved
  readability on wall-mounted displays viewed at distance
- Card elevation ladder smoothed to consistent ~1.5x geometric
  progression: RECESSED 0.03→0.04, BASE 0.06→0.07,
  ELEVATED 0.10→0.11, HEADER 0.17→0.16

### Added
- FONT_STACK_SERIF token: Georgia, "Times New Roman", serif
  Promoted from daily-message-display inline usage to shared token

### Removed
- constants.js fully retired — all workers now import from colors.js

## - v0.6.4 - test auto delete branch
- Test auto delete branch created on auto merge of utils updates

## v0.6.3 - update accent color
- Update accent color to #FF0000 to match display hardware theme exactly

## v0.6.2 — retire constants.js
- Removed DARK_BG_COLOR export from constants.js
- All workers now import DARK_BG_COLOR from colors.js directly
- constants.js deleted

## v0.6.1 — TEXT_SUPPORTING token
- Added TEXT_SUPPORTING = rgba(255,255,255,0.75) to colors.js
- Mid-opacity text level between TEXT_SECONDARY and TEXT_PRIMARY
- Used for rank text, field values, and supporting content

## v0.6.0 — design tokens
- Added utils/colors.js with DARK_BG_COLOR, FONT_STACK, ACCENT_COLOR,
  text/border/card elevation tokens
- Added utils/layouts.js with LAYOUTS object and DEFAULT_LAYOUT
- Added utils/alert-colors.js with NWS alert severity color sets
- constants.js unchanged — DARK_BG_COLOR remains there until all
  workers are migrated to import from colors.js, then it will be retired

## v0.5.0 — rotation helpers
- Added utils/rotation.js with getTodayString, getDaysElapsed,
  getBlockIndex, getSecondsUntilNextRotation, formatHireDate
- All functions accept parameters instead of reading module-level
  constants, making them reusable across workers with different
  rotation anchors and times
- DST-safe via Intl.DateTimeFormat with America/Chicago timezone

## v0.4.0 — google-auth
- Added utils/google-auth.js with getAccessToken
- Accepts scope as a parameter so one function serves all Google API use cases
- Includes base64url and arrayBufferToBase64url helpers
- Uses Web Crypto API — no external dependencies

## v0.3.0 — html helpers
- Added utils/html.js with escapeHtml and sanitizeParam
- escapeHtml: prevents XSS by escaping HTML special characters
- sanitizeParam: strips non-alphanumeric characters from URL parameters

## v0.2.0 — fetch-helpers
- Added utils/fetch-helpers.js with fetchWithTimeout
- Wraps fetch() with AbortController timeout to prevent Workers hanging on stalled upstream endpoints
- Default timeout: 8000ms; token exchanges should use 10000ms

## v0.1.0 — initial
- Created repository structure
- Added utils/constants.js with DARK_BG_COLOR
