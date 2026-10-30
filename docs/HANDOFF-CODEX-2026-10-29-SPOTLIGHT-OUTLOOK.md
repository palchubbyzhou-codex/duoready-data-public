# Handoff to Codex — 2026-10-29: Publish DuoReady Spotlight No. 1 (Outlook), now

**From:** Muse (data + verification) · **Requested by Jie:** "现在就做" — please build and publish in this round.

## Task 1 — Publish the Outlook Spotlight feature

Source package (final, Jie-approved copy — polish for tone only, do not change facts, scores, or claims):
- `features/spotlight/outlook/feature-en.md`
- `features/spotlight/outlook/feature-zh.md`
- `features/spotlight/outlook/compare-slab-vs-duo-en.png` / `compare-slab-vs-duo-zh.png` (original illustrations — keep the "illustration, not a screenshot" labeling from the copy)
- `features/spotlight/outlook/research-dossier.md` (evidence file; not for publication)

Format spec (fixed for the whole series): `docs/SPOTLIGHT-FORMAT.md`
- Series names: EN **DuoReady Spotlight** · ZH **DuoReady 特写**
- Build the section entry in the same round: homepage + directory-top Spotlight card (icon + one-line verdict + score → feature page), "Spotlight / 特写" marker on the Outlook directory row linking to the feature page, "More Spotlight features" cross-link slot at the feature page bottom.
- Suggested routes: `/spotlight/outlook/` (ZH default) + `/en/spotlight/outlook/`; add both to the sitemap.
- Score on the page: 3/5 = 60/100, status "Partially adapted / 部分适配", tier verified. The Outlook DB record is already in `data/apps.json` (slug `outlook`, listed_on_site true) and syncs through the normal pipeline.

## Task 2 — Fix the Ask Chubby US-market record link

From `docs/VERIFICATION-PER-APP-PAGES-2026-10-29.md`: for US-store answers, the record link points to the directory search anchor instead of the app page (CN-store already links correctly). Make US/default-market answers link to `/apps/<slug>/` the same way.

## Report back (for Muse's verification)

- The two live feature URLs + sitemap total after the change
- Confirmation the Spotlight card/marker is live
- One US-store Chubby answer (e.g. Airmail) showing the corrected page link

Muse will re-verify live: feature pages vs the package copy (facts/score/sources unchanged), section entry present, Chubby US + CN link behavior, and no unlisted-app links introduced.
