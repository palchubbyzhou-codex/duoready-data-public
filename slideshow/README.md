# slideshow/ — DuoReady news slides (pipeline)

How publishing works:
1. The assistant (Muse) creates each slide as a PNG pair — English (`-en.png`) and Chinese (`-zh.png`), 1920×1080 — written in DuoReady's own words from a credible source, with the source credited on the slide itself.
2. The assistant drops the PNGs into this folder and registers them in `slides.json` (newest first), then pushes. HTML sources live in the private repo under `slideshow/src/`.
3. The website (Codex) reads `slides.json` from the public mirror at runtime:
   https://raw.githubusercontent.com/palchubbyzhou-codex/duoready-data-public/main/slideshow/slides.json
   Image paths in the manifest are relative to the public repo root.
4. Display rules: show `image_zh` when the site language is Chinese, `image_en` otherwise; the whole slide (or a Read-more control) links OUT to `source_url` — slides are summaries, never copies of the source article; keep the on-slide source credit visible (do not crop the footer).
5. Codex does not edit images or manifest entries. New slides arrive only via the assistant's pushes; Jie approves topics.
