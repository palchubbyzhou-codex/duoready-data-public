# slideshow/ — DuoReady news banners (pipeline)

## Current standard (Codex spec, 2026-10-28 — supersedes the 16:9 slide format)
Each story ships as FOUR WebP files, named `YYYY-MM-DD-topic-{en|zh}-{desktop|mobile}.webp`:
- **Desktop: 2400×800 (3:1)** banner master. The site renders it responsively (fixed height ~287px, width varies) as "text + product image".
- **Mobile: 1080×1080 (1:1)** — a genuine re-layout for square, NOT a crop of the desktop file. Site renders at fixed height ~300px.
- EN and ZH versions of each. Square corners in the files (the site applies its own rounding). No carousel dots/buttons baked in. Text and logo keep ≥5% margin from edges. Source + image credit are printed on every file.

## How publishing works
1. The assistant (Muse) creates the 4 files in DuoReady's own words from a credible source, drops them in this folder, and registers them in `slides.json` (newest first), then pushes. HTML sources live in the private repo under `slideshow/src/`.
2. The website (Codex) reads `slides.json` from the public mirror at runtime:
   https://raw.githubusercontent.com/palchubbyzhou-codex/duoready-data-public/main/slideshow/slides.json
   Image paths are relative to the public repo root. Fields: `image_en_desktop`, `image_zh_desktop`, `image_en_mobile`, `image_zh_mobile` (legacy `image_en`/`image_zh` 1920×1080 exist for the first story only — prefer the four new fields when present).
3. Display rules: desktop vs mobile by viewport, ZH vs EN by site language; the whole banner (or a Read-more control) links OUT to `source_url` — banners are summaries, never copies of the source article; keep the on-image source credit visible.
4. Codex does not edit images or manifest entries. New banners arrive only via the assistant's pushes; Jie approves topics.
