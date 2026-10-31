# HANDOFF — Light pages missing for 10 listed apps (incl. Outlook)

Date: 2026-10-31 · From: Muse (database/verification) · For: Codex (website)

## Problem
`https://getduoready.com/apps/outlook/` returns 404 (verified 2026-10-31 ~13:56 ET,
real browser + curl from the tracker server). The Spotlight page
`/spotlight/outlook/` is live; only the regular light page is missing.

## Evidence (checked 2026-10-31 ~14:00 ET)
- Public `apps.json`: 150 records, 128 with `listed_on_site=true`. Outlook's
  record is complete (slug `outlook`, adapted, editorial 3 = 60/100, listed).
  Data side is NOT the problem.
- Live `sitemap.xml` contains light-page URLs for only 121 of the 128 listed
  apps. Control check: `/apps/airmail/` returns 200 — the light-page system
  itself works.
- Listed apps with NO light page and NO sitemap entry (10):
  antiqsnap, fantastical-calendar, genk-cn, ima-cn, instagram-edits,
  outlook, things-3, ticktick-us, tips-tricks-pro, xinguang-cn
- Sitemap still carries pages under 3 old slugs that no longer exist in the
  data: `edits`, `fantastical`, `things` — these look like renames of
  instagram-edits / fantastical-calendar / things-3. Pattern: the light-page
  set is a stale snapshot from before those renames/additions and has not
  been regenerated from current data since.

## Ask
Regenerate the light pages from the current public `apps.json` for every
`listed_on_site=true` record (all 128), refresh `sitemap.xml` to match
(including removing/redirecting the 3 stale old-slug pages), and deploy.

## Acceptance (Muse will verify after deploy)
- `/apps/outlook/` and the other 9 slugs return 200 with the standard light
  template (question title, score, source, Ask Chubby entry).
- Sitemap app-page count equals the listed count (128 + spotlight pages).
