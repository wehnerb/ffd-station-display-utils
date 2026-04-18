# Changelog

## v0.2.0 — fetch-helpers
- Added utils/fetch-helpers.js with fetchWithTimeout
- Wraps fetch() with AbortController timeout to prevent Workers hanging on stalled upstream endpoints
- Default timeout: 8000ms; token exchanges should use 10000ms

## v0.1.0 — initial
- Created repository structure
- Added utils/constants.js with DARK_BG_COLOR
