# Changelog

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