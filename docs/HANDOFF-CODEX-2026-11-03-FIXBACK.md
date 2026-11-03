# HANDOFF — FIX-BACK: 2026-11-03 verification of the latest deploy

Issued by: assistant (Muse), after Jie asked for a post-fix audit on 2026-11-03.
Verified live on getduoready.com at ~17:00 ET, 2026-11-03 (served HTML, CSS,
sitemap, rendered store page, repo JSON cross-check).
This is a fix-back on work orders #8, #9 and SEO plan P0 (#6). Items marked
verified-OK at the bottom need no work — do not redo them.

## FB-1 (P0, = #8 / #9 P1-3, STILL OPEN) — "10 minutes" copy everywhere

Poll cadence has been 5 minutes since 2026-11-02. Served HTML today:

- Homepage `/`: 4 occurrences — "refreshes every 10 min" ×1,
  "every 10 minutes" ×3
- `/stock/`: 4 occurrences of "every 10 minutes"; zero "every 5 min"

Acceptance: `grep -i "10 min" `over the served HTML of `/` and `/stock/`
returns nothing; any countdown/sweep display caps at 05:00. This item has
now failed verification twice (2026-11-03 09:30 and 17:00) — please fix it
in the template/source, not per-page.

## FB-2 (P0, new pages) — store pages render a failure string as status

Sampled live page `/stock/store/florida-mall/` (crawled 2026-11-03 22:01 UTC)
shows under "Latest inventory check":

> "Availability temporarily unconfirmed."

This is the exact loading-failure wording #9 P2-6 exists to eliminate, now
server-rendered into indexable SEO pages. Store pages must render a
definitive state from /api/snapshot.json (CORS open):

- In stock: models + "checked HH:MM ET"
- Not in stock: "Out of stock — last checked HH:MM ET"

"Unconfirmed" may exist only as a transient client-side state during a
live fetch; it must never be the server-rendered content. If the snapshot
endpoint is down, omit the status block — do not print a failure sentence.

## FB-3 (P0, = #9 P0-1, root cause unchanged) — directory card geometry

`/readability.css` as served today still contains:

- `.directory .apps { grid-auto-rows: 112px; ... }`
- `.directory .app { min-height: 112px; ... }`

That fixed 112px row is the named root cause of mobile cards clipping
their status line (cards need ≥147px on mobile, per the #9 audit).
Acceptance: rows size to content (auto) or ≥ the tallest card; verified
by a 390×844 screenshot where every visible card's full status line shows.
If the card design was deliberately reworked to fit 112px, say so in the
workorder log and the screenshot check becomes the acceptance test.

## FB-4 (P1, = #6 / SEO TOP plan P0) — store matrix is a 10-page pilot

Live in sitemap (278 URLs total): exactly 10 store pages —
florida-mall, northpark-center, rosedale-center,
the-fashion-mall-at-keystone, boca-raton, brickell-city-centre,
lincoln-road, millenia, st-johns-town-center, aventura.
Remaining: 244 of 254. Ship them from stores.json (regenerated daily by
the pipeline) per the P0 template in
docs/HANDOFF-CODEX-2026-11-03-SEO-TOP.md. City hub pages: still 0.

## FB-5 (P1) — pilot store pages are missing the template's core blocks

On the Florida Mall sample, the following are absent (all data exists):

- FAQ block (3–4 Q&A + FAQPage schema)
- Verified outcomes — our differentiator — from /api/verify-stats.json
  (e.g. share of drops verified sold out, verification stamps)
- stores.json fields already on disk but unused: `peak_window`
  ("2 PM – 5 PM ET"), `fastest_gone_min` (10)
- Nearby-stores internal links (only one "Compare other stores" link now)

A store page that is only title + status + two restock sentences will
read as a thin doorway page. Build the full template once, then let
FB-4's remaining 244 pages inherit it.

## FB-6 (P2) — configuration list contradicts the restock count

Florida Mall page: "6 restocks" but "Reported configurations: 256GB
Star White, 512GB Night Sky" only. stores.json `last_drop_models` for
this store carries 6 entries — the 2 named configs plus 4
"Variant X4 (config TBD)" entries the page silently drops.
Rule (unchanged): never invent a variant name. Either list all recorded
entries with their TBD labels, or write "2 confirmed configurations
(+4 unconfirmed variants)". Counts and lists must agree.

## Not yet verifiable by text fetch — needs a rendered check

- #9 P0-2: directory pagination → mobile continuous scroll. The served
  /apps/ HTML contains no pagination markup (client-rendered), so this
  could not be confirmed either way.
- #9 P1-7: tracker panel dark-mode palette. Needs a screenshot pass.

Close both by posting before/after screenshots in the workorder log, or
leave them open for an assistant screenshot audit.

## Verified OK on 2026-11-03 — no action

- Data invariants: apps.json 191 = scores-100.json 191, score_100 =
  editorial_score × 20 with 0 mismatches; stores.json 254; news.json 115.
- Favicon serving (200, image/vnd.microsoft.icon).
- Footer: the stale "Directory updated: Oct 30, 2026" string is gone.
- /stock/ hub links to all 10 live store pages.
- Store-page restock figures are faithful to stores.json (Florida Mall:
  6 drops / 7d, last 2026-10-30 11:15 PM ET — matches the file exactly).
- Homepage: "temporarily unconfirmed" no longer appears in served HTML.

## Process note

As of 2026-11-03 17:00 ET the two data repos show no Codex commits after
the assistant's 16:03 push — website deploys evidently happen outside
these repos, which is fine. Reminder: runtime JSON files in these repos
are pipeline-owned; please keep reading them, never hand-editing them.
