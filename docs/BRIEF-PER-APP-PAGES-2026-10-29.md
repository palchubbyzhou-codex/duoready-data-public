# Brief for Codex: Per-App Light Pages (Bulk Generation)

**Date:** 2026-10-29
**From:** Muse (data owner) via Jie
**Scope approved by Jie:** Bulk light pages ONLY. Not in scope: deep/editorial pages, UGC submission features, any design changes, any data-field changes.

## Problem

The sitemap currently lists 28 URLs. Only **9 apps** have their own page:
things, xmind, timepage, edits, nyt-cooking, fantastical, rednote, qq-music, tencent-video.

apps.json holds **137 records** (121 with `listed_on_site: true`). The other 112 listed apps exist only as rows on the directory pages. Google cannot rank a directory row for a query like "does TikTok work on iPhone Duo" — there is no URL to rank. We are invisible for most of the questions we actually have data for.

## Task

Generate one light page per listed app from apps.json, following the exact route pattern of the existing 9:

- `/apps/<slug>/` and `/en/apps/<slug>/` for every app with `listed_on_site: true`
- `/zh/apps/<slug>/` with the Chinese fields (see language rules below)
- Apps with `listed_on_site: false` (16 records): **no page, no sitemap entry.** That flag is Jie's publishing control; respect it exactly.

Expected result: sitemap grows from 28 to roughly 28 + (121 × 3 − existing) ≈ **380 URLs**.

## Data source

Public mirror `apps.json` (same file the site already reads at runtime). Fields available per record:

`slug, name_en, name_zh, aliases, store (US/CN), category, status, adaptation_en, adaptation_zh, editorial_score (1–5), highlights[], listed_on_site, source_name, source_url, credibility_tier, date_verified`

Note: `adaptation_zh` is present for 101 of 137 records. See language rules for the fallback.

## Page template (light page — this is a doorplate, not an article)

Every page must contain ALL of the following. No page may ship as an empty shell.

1. **Title tag:** EN: `Does {name_en} work on iPhone Duo? Adaptation score {score_100}/100 — DuoReady` · ZH: `{name_zh or name_en} 在 iPhone Duo 上适配怎么样？评分 {score_100}/100 — DuoReady`
   - `score_100 = editorial_score × 20` (pure linear rescale per `docs/SCORE-CARD-100.md` / `data/scores-100.json`. Never recompute differently, never blend in credibility tier.)
2. **Meta description:** one line built from status + adaptation text (truncate `adaptation_en`/`adaptation_zh` to ~150 chars).
3. **H1:** `{name} on iPhone Duo`
4. **Verdict block:** status rendered as a plain-language line (e.g. "Adapted for iPhone Duo" / "Not yet adapted"), plus the score shown as the 100-point number with the 5-point value beside it (e.g. `80/100 (4/5)`).
5. **Body paragraph:** `adaptation_en` (EN pages) / `adaptation_zh` (ZH pages) verbatim from the data. If `highlights[]` is non-empty, render as a short bullet list under it.
6. **Source line:** `Source: {source_name}` linking to `source_url`, plus credibility tier and `date_verified`, rendered the same way the directory renders them today. This line is mandatory — it is our credibility rule, not decoration.
7. **Funnel CTAs (the point of these pages):**
   - Primary button: back to the full directory (`/apps/` or `/apps/china/` by store, language-matched)
   - Secondary: homepage
   - Ask Chubby link with the question prefilled for this app (same mechanism the chat already supports; if prefill is not supported, link to `/chubby/` plain)
8. **Related apps:** 3–5 links to other per-app pages in the same `category` (internal linking so Google can crawl the whole set from any single page).
9. **Structured data:** `WebPage` + `SoftwareApplication` JSON-LD with name, and the score as `aggregateRating`-free plain properties — do NOT mark the editorial score up as a review/aggregate rating; it is an editorial score, keep it honest.

## Language rules

- EN pages: `name_en`, `adaptation_en`.
- ZH pages: `name_zh` when present, else `name_en`; `adaptation_zh` when present, else fall back to `adaptation_en` untranslated (do not machine-invent a translation, do not leave the body empty).
- CN-store apps get all three routes too (the existing rednote/qq-music/tencent-video pages already set this precedent).

## Hard rules

- **Render only what the data says.** No invented layout details, no invented version numbers, no padding copy written to make pages look fuller. If a field is null, omit that element.
- **No changes to apps.json field structure** (per `docs/chubby-collaboration.md`, field changes need coordination with the data owner first).
- **No visual/design changes** to the existing template system; reuse the existing app-page layout used by the 9 live pages.
- New pages must be picked up automatically by the daily data pipeline: when apps.json gains a record with `listed_on_site: true`, its pages should exist without manual steps (generate at build/publish time from the same JSON).
- Add every generated page to `sitemap.xml` automatically.

## Deliverables / report back

1. Count of pages generated, broken down by route (default / en / zh) and store.
2. The full updated sitemap URL count.
3. 3 sample URLs (one US app EN, one CN app ZH, one not_adapted-status page if any listed app has that status).
4. Confirmation that the 16 `listed_on_site: false` apps produced no pages.

Muse will verify after publish: sitemap count, spot-check 5 pages against apps.json (score, source line, status), and confirm no unlisted app leaked in.

## Out of scope (do not build)

- Deep/editorial per-app pages (separate future brief).
- User screenshot/video submission (UGC) features.
- Any change to Ask Chubby, the directory pages, or the homepage.
