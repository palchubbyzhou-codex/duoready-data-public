# HANDOFF — SEO TOP Plan: outrank the stock-tracker SERP (2026-11-03)

Owner: Jie decision 2026-11-03 ("拆他们 SEO 模式，写 Codex 计划，我要让我们的网站置顶").
Executor: Codex (website). Data/prep: assistant. This extends work order #6 (store
matrix) — #6's stores.json is the data foundation; this plan is the full build-out.

## 0. Objective

Rank DuoReady #1 (minimum: page 1, top 3) on Google for the stock-tracker
query family, US first:

- "iphone duo stock tracker", "iphone duo in stock", "iphone in stock tracker"
- "iphone duo stock <city>" / "apple <store> iphone duo stock" long tail
- "when does apple restock iphone duo", "how long does iphone duo stock last"

## 1. Evidence — the top 3 and how they win (dissected 2026-11-03)

Google for this query family is owned by three tracker sites. Their sitemaps
were enumerated and classified on 2026-11-03:

| Site | Indexed URLs | Matrix |
|---|---|---|
| instockradar.com | **6,290** (26 country sub-sitemaps) | store×model 1,557 (+~1,365 language variants es/en/fr) · store hubs 520 · store /restocks 514 · city pages 113+ · country×model /restocks + "when does it restock" + "how long stock lasts" data pages |
| manzanatracker.com | **2,653** | product×country×city (420 for the phone line) — same template engine replicated across ~20 Apple product lines (AirPods, Watch, Vision Pro, HomePod…), 60 city pages each |
| storestockchecker.com | **1,018** | model×country×city 117 · model×place /restocks 84 · hundreds of /{model}/near/{store}/restocks long-tail pages |
| **getduoready.com (us)** | **268** | app directory + hubs; stock section = 2 URLs (/stock/, /zh/stock/); **store pages: 0** |

Winning patterns (structure observed on their pages; patterns, not copy):

1. **One URL per real-world entity**: every store, every city, every model gets
   its own crawlable page. The matrix IS the strategy — thousands of long-tail
   queries each land on an exact-match page.
2. **Title formulas**: "iPhone Duo in stock in <City>: live Apple Store stock
   checker" / "<Model> stock tracker in <Country>: who has it in stock near
   me" / "When does Apple <Store> restock iPhones?" — query-shaped titles.
3. **Every page carries live, changing data** (current status, last restock,
   per-store history) → freshness signals + a reason to re-crawl daily.
4. **Data pages as link bait**: /restocks statistics ("53% of restocks land
   9:30–11:00 AM", "typical time in stock: 1 min") explicitly "free to quote
   with a link" — built to earn citations.
5. **Hub hierarchy**: country → model → city → store, dense internal links,
   nearby-stores cross-links on every store page.
6. Language variants multiply the matrix (ISR es/en/fr) — later phase for us.

## 2. Our assets (why we can win pages they can't)

- stores.json already generated daily: 254 US stores, per-store drop history
  (141 stores with drops, 244 restocks / 7 days) — work order #6 data is DONE.
- **Verification data nobody else has**: our verifier re-checks every drop on
  Apple's official feed (424 restocks logged, verified/sold-out outcomes,
  survival timing). ISR/SSC/Manzana show poller data only. "Verified on Apple"
  per-store stats are a genuine content differentiator, not a template clone.
- Chance Index + peak-window statistics from our own archive (Oct 24 →).
- Live endpoints already public: /api/snapshot.json, /api/verify.json,
  /api/verify-stats.json, /api/history — pages can render real status.

## 3. Build phases

### P0 — US store pages (the missing dimension) — first
- 254 pages: `/stock/store/<store-slug>/` (EN; zh after P1 proves out).
- Template (write fresh copy; do NOT reuse competitor text):
  - Title: "iPhone Duo at Apple <Store> (<City, ST>) — Live Stock & Restock History | DuoReady"
  - H1: store name + city. Live status block (in stock now? models, checked
    HH:MM ET) rendered server-side from snapshot at build/crawl time + client
    refresh.
  - Restock history table (date/time, models, how long it lasted, verified
    outcome) from stores.json + history archive.
  - Store facts: address, store number, peak restock window for this store,
    drops in last 7/30 days, fastest gone.
  - FAQ block (3–4 Q&A with FAQPage schema): is it in stock, when does this
    store restock, how fast does it sell out, how DuoReady verifies.
  - BreadcrumbList schema; nearby stores (same metro) internal links ×6–10;
    link up to city hub + model hub.
- Sitemap: new sub-sitemap /sitemaps/stock-stores.xml, <lastmod> = last
  restock or daily.

### P1 — Hubs
- City pages for every US metro with ≥1 store (~120): `/stock/<city-slug>/` —
  title formula "iPhone Duo in stock in <City>: live Apple Store stock
  checker" pattern, live store list, city restock stats, peak window.
- State pages where a state has ≥3 stores. Model hub upgrade of /stock/
  (current live board + today stats + links down to every city).
- Internal linking: homepage stock panel → /stock/ → city → store, no page
  deeper than 3 clicks from home.

### P2 — Data pages (link bait, our verified angle)
- `/stock/restocks/` US statistics: drops by hour (ET), survival distribution,
  % verified sold out within 5 minutes, top stores — from OUR archive, marked
  "free to quote with a link".
- Per-city "when does <City> restock" sections can fold into P1 city pages.
- Duo News weekly flagship links into these pages (existing pipeline).

### P3 — Indexation & hygiene
- Split sitemap index (core / apps / stock-stores / stock-cities), submit in
  GSC, monitor coverage weekly via the existing Monday SERP watch
  (duoready-serp-watch cron) — extend its keyword set with 10 city long-tails.
- Canonical rules, no parameter duplicates; zh variants only after EN indexes.

### P4 — Only after US proves out (do not start early)
- More models (18 Pro / Pro Max) on the same engine; more countries;
  language variants. Manzana's breadth is a phase-2 weapon, not phase 1.

## 4. Guardrails

- Patterns yes, text no: every title/body is our own writing. No copied
  sentences, tables, or FAQ text from the three sites.
- No thin doorway pages: a store page ships only with its real history +
  live status wired. If a store has zero drops ever, it still carries live
  status + city stats — never an empty shell.
- Runtime JSON files (apps.json etc.) are pipeline-owned; this work reads
  them, never hand-edits them. stores.json generation stays in the daily job.
- Duo News publishing rules unchanged.

## 5. Acceptance / measurement

- P0 done = 254 store URLs live, in sitemap, sampled 10 pages show correct
  live status vs /api/snapshot.json, titles per formula, PageSpeed sane.
- Weekly (existing SERP watch): track the 6 core terms + 10 city long-tails;
  baseline 2026-11-02 = absent on core terms. First checkpoint: any core
  term on page 1 within 4 weeks of P0+P1 shipping; #1 is the goal, expect
  weeks-to-months — ISR's moat is matrix × freshness × time, and P2's
  verified-data angle is our shortcut to citations.
- Report deltas only; silence when nothing moved (standing rule).

## 6. Inputs on disk

- stores.json (public repo root, regenerated daily) — per-store stats.
- Server endpoints: /api/snapshot.json, /api/verify.json,
  /api/verify-stats.json, /api/chance-index.json (CORS open to
  getduoready.com).
- SERP baseline log: assistant-side duoready-watch/serp/log.md.
