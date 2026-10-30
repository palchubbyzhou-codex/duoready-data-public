# Handoff for Codex — Add the DuoReady favicon (2026-10-30)

## What Jie picked
Candidate **B**: white "duo" letters on near-black (#0A0C12), full-bleed square.
Made from the official 6000px wordmark ("duo" split off, inverted to white).
Other candidates (Chubby face / full wordmark / full badge) were shown at true
16px size and rejected — the wordmark turns to mush at tab size.

## Files (in this folder's `favicon/` subfolder)
- `favicon.ico` — multi-size 16/24/32/48/64
- `favicon-16x16.png`
- `favicon-32x32.png`
- `apple-touch-icon.png` — 180×180
- `android-chrome-192x192.png`
- `android-chrome-512x512.png`

## To do (site root, ~2 minutes)
1. Copy all six files to the site root (same level as `index.html`), so they
   resolve at `https://getduoready.com/favicon.ico` etc. The `.ico` MUST sit
   at the root path — browsers request `/favicon.ico` by convention even
   without a link tag.
2. Add to `<head>` on every page (or the shared layout/template):

```html
<link rel="icon" href="/favicon.ico" sizes="any">
<link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png">
<link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png">
<meta name="theme-color" content="#0A0C12">
```

3. If a `manifest.webmanifest` / PWA manifest exists, also add:

```json
{ "src": "/android-chrome-192x192.png", "sizes": "192x192", "type": "image/png" },
{ "src": "/android-chrome-512x512.png", "sizes": "512x512", "type": "image/png" }
```

## Verify after deploy
- `https://getduoready.com/favicon.ico` returns 200 (currently 404 — that's
  why tabs show the generic globe).
- Hard-refresh the homepage: tab shows the black square with white "duo".

## Notes
- Do not redraw or substitute the artwork — use these files as-is
  (official-logo rule). If an SVG version is ever wanted, it must be traced
  from the official wordmark, not retyped in a similar font.
- Assistant will verify live after deploy (favicon 200 + tab check).
