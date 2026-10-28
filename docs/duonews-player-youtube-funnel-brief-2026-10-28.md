# Duo News Module — YouTube Funnel Format (Codex Brief, 2026-10-28)

**Goal:** turn the existing THE DUO NEWS module into a YouTube funnel. The on-site player is the teaser; YouTube is the destination.

**Hard constraint:** the homepage layout and story do NOT change. Same module, same position, same player size. Everything below happens *inside* the existing news module. Nothing else on the page is touched.

## 1. Data source — episodes.json (already seeded, do not hardcode episodes)

The module reads its episode list at runtime from:
`https://raw.githubusercontent.com/palchubbyzhou-codex/duoready-data-public/main/episodes.json`
(same pattern as apps.json / kits.json / news.json / basic-chat.json; newest episode first).

Schema:
```json
{
  "version": 1,
  "channel_shorts_url": "https://www.youtube.com/@DuoReady/shorts",
  "episodes": [
    { "ep": 3, "youtube_id": "Fe-OSEWnFqQ", "url": "https://www.youtube.com/shorts/Fe-OSEWnFqQ",
      "format": "breaking", "date": "2026-10-28",
      "title_en": "BREAKING: Ask Chubby Is Live — The Dog Who Answers Your Duo Questions",
      "title_zh": "突发：Ask Chubby 上线——会回答 Duo 问题的狗" }
  ]
}
```
Seeded today with Ep.1–Ep.3. New episodes arrive as data updates only — after this change, **no code change may be needed to add an episode**.
Fallback: if the fetch fails, keep the current hardcoded behavior (Ep.1 + Ep.2) so the module never renders empty.

## 2. Player — newest first

- Load `episodes[0]` (the newest). Muted autoplay, playsinline — as today.
- When an episode ends, advance to the next older one; after the oldest, loop back to the newest. (This replaces the current oldest-first playlist loop: Ep.1 → Ep.2 becomes Ep.3 → Ep.2 → Ep.1 → Ep.3…)

## 3. THE button — Watch on YouTube (the point of this brief)

- One button, full module width, directly under the player.
- Style: YouTube red background, white bold text, with a ▶ glyph. Label: EN `▶ Watch on YouTube` / ZH `▶ 去 YouTube 看`.
- The button links to the **currently playing** episode's `url` from episodes.json, opens in a new tab (`target="_blank" rel="noopener"`).
- Whenever the playing episode changes (auto-advance or any future switch), the button's target updates to match. The button must never point at a different episode than the one on screen, and never at a hardcoded ID.

## 4. Previous-episode rows — every row links OUT to YouTube

- Under the button, up to 2 rows: `episodes[1]` and `episodes[2]`.
- Each row: thumbnail (`https://i.ytimg.com/vi/<youtube_id>/hqdefault.jpg`), `EP.0X` label, title (`title_en` / `title_zh` by site language), format tag (BREAKING = red, WEEKLY = blue), date.
- The whole row is a link to that episode's YouTube `url`, new tab. Rows do **not** load anything into the on-site player — they exist to send viewers to YouTube.
- Final row under them: `More episodes on YouTube →`, linking to `channel_shorts_url`, new tab.

## Acceptance checks

1. Fresh page load: Ep.3 (Ask Chubby) plays first, muted, no layout change anywhere else on the homepage.
2. The red button under the player opens `https://www.youtube.com/shorts/Fe-OSEWnFqQ` in a new tab.
3. When the player advances to Ep.2, the button then opens Ep.2's YouTube page (sPjslX3DuCQ) — never a stale target.
4. Two previous rows (Ep.2, Ep.1) render with thumbnails and format tags; each opens its own YouTube page in a new tab; the "More episodes" row opens the channel Shorts page.
5. Chinese mode: button label and row titles switch to the `_zh` strings.
6. Adding a new first entry to episodes.json (no deploy) makes it the featured episode, the button target, and shifts the rows down.
