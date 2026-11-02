# Handoff for Codex — New homepage: mobile fixes (audit 2026-11-02 evening)

Source: Muse live audit of https://getduoready.com/ after the redesign launch (code inspection of the served CSS/JS + rendered check + Jie's own iPhone screenshots). 85% of DuoReady users are on phones — mobile is the primary surface. Verify every fix at 390×844 before calling it done.

## P0-1 — Directory cards: status line clipped by the next row (mobile)
- Symptom (Jie's screenshot): in the A–Z grid on phones, every card's green status line ("Adapted") is cut in half / covered by the card below.
- Root cause found in served CSS: legacy `readability.css` sets `.directory .apps{grid-auto-rows:112px}` and `.directory .app{min-height:112px}`, while the redesign's mobile card (`.redesign-home .app`, ≤500px) is a vertical layout with `min-height:147px` (62px icon + name + `.status`). Content overflows the fixed 112px row by ~35px; the next row's card background paints over it. Desktop uses the horizontal card, which fits — that is why it only breaks on phones.
- Fix: rows must size to content (e.g. `grid-auto-rows:auto` for the directory grid, or a row height that fits the tallest card incl. status). Acceptance: at 390px wide, the status line of EVERY card is fully visible, no overlap anywhere in the grid.

## P0-2 — Directory pagination + dead space on mobile
- The directory paginates at 18 apps/page (7 pages); page 1 ends at "Crossy Road Castle" (C). On a phone this reads as "the list just ends", and after the last row there is a long dead stretch before the pagination controls / footer (Jie: "下面的空白往下拉太多了"). On desktop the same gap measures only ~0.2–0.3 screen — something in the mobile flow stretches it. Prime suspect in served CSS: legacy `.feature.things-feature{min-height:650px;padding-bottom:330px}` (readability.css) is still loaded — check whether that section/rule sits in the page flow.
- Fix: no dead vertical space — pagination directly under the grid on mobile; strongly consider continuous scroll loading instead of ?page=N reloads. Acceptance: on a 390×844 phone, after the last card row the pagination/footer follows within ~40px; page 1 no longer looks like the end of the directory.

## P1-3 — "Every 10 min" copy + panel cadence still 10 minutes (= open workorder #8)
- The new homepage still says "Live 24/7 · refreshes every 10 min" (3 occurrences in the served HTML), and the stock panel's own refresh countdown runs ~10 minutes (observed resetting to ~09:17 after a snapshot), even though /api/snapshot.json data now updates every 5 minutes.
- Fix: copy to 5 minutes everywhere on the homepage, and the panel fetch/countdown cadence to 5 minutes. Acceptance: panel countdown never exceeds 05:00; no "10 min" string remains on the homepage.

## P1-4 — Floating sticky nav covers content while scrolling
- The glass nav pill stays fixed and section headings / card tops slide underneath and get covered (seen on desktop and in Jie's phone screenshots, where it eats the top card row). On phones the usable viewport is already small.
- Fix: content must never be hidden under the bar (scroll-margin-top on sections, or a bar that turns solid/shrinks on scroll). Acceptance: scrolling at 390px wide, no heading or card top is ever covered by the nav.

## P2-5 — Footer freshness date contradicts the data
- Footer says "Directory updated: Oct 30, 2026" while the directory shows an Oct 31 "New to DuoReady" batch and data updates daily. Make the date data-driven or drop it.

## P2-6 — Loading states look like failures
- First paint shows "Data temporarily unconfirmed" / "Snapshot updated · awaiting data", and app icons flash as blank white squares (seen on page 2). On mobile networks this lasts longer and reads as "data is broken" for a stock tool. Use neutral skeleton states; reserve "unconfirmed" for actual stale data.

## Notes (no action)
- THE DUO NEWS module is live as a placeholder ("The next edition") — expected; the first piece publishes once Jie supplies its images.
- The SEO store-page matrix (workorder #6) did NOT ship in this release: sitemap still lists only /stock/ (no per-store pages).
- Data itself is healthy: /api/snapshot.json and /api/verify.json return current data (verified 2026-11-02 ~17:00 ET); the verification panel shows real drops (e.g. Reno Shayden Summit, Nov 2, 3:08 PM ET, SOLD OUT).


## P1-7 — Tracker panel in dark mode: colors clash, panel looks hollow (added 2026-11-02 17:43, from Jie)

Evidence: Jie's screenshot `docs/jie-darkmode-tracker-2026-11-02.png` (homepage stock panel, dark theme, snapshot Nov 2, 05:41 PM ET).

- Three stacked dark shades that do not belong to one palette: outer container, near-black left panel, lighter blue-grey verification card — the right card looks pasted in.
- The left panel is mostly an empty dark void: the "Next refresh" area renders as a tiny line-and-dot glyph, so the panel reads as broken/half-loaded instead of designed.
- Accents clash with the surfaces: bright-blue CTA pill and the red SOLD OUT stamp sit on muted greys with no shared palette; nothing matches the site's dark theme elsewhere.
- In the screenshot the panel headlines "Data temporarily unconfirmed" even though its own snapshot timestamp is current (05:41 PM ET) — with 0 stores in stock it should settle on the "No stock in the latest snapshot" state, not the alarming unconfirmed state (relates to P2-6).

Fix: give the tracker/verification panels one coherent dark palette aligned with the site dark theme (single surface family, consistent borders), fill or rebalance the left panel so it never looks hollow, and align accent usage. Acceptance: screenshot the panel at 390px and desktop in dark mode — one palette, no void, no "unconfirmed" headline when the snapshot is fresh.

