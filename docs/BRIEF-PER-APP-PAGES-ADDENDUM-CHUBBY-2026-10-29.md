# Addendum to BRIEF-PER-APP-PAGES-2026-10-29: Ask Chubby must learn the per-app pages

**Date:** 2026-10-29 · **Requested by Jie** · Companion to `docs/BRIEF-PER-APP-PAGES-2026-10-29.md`

The per-app light pages and Ask Chubby must link to each other in BOTH directions. The main brief already covers page → Chubby (prefilled-question link in each page's CTA block). This addendum covers the reverse:

## Requirement: Chubby → per-app page links

1. Every Ask Chubby answer that names a specific app which HAS a per-app page must include a visible link to that page: `/apps/<slug>/` (route matched to the conversation language: ZH conversation → `/zh/apps/<slug>/`, EN → `/en/apps/<slug>/` or default route, same pattern as the site).
   - Label: EN "Full adaptation page →" · ZH "查看完整适配页 →"
   - This applies to direct lookups ("Is Outlook adapted?") AND to recommendation answers (each recommended app in the list gets its own page link).
2. Apps with `listed_on_site: false`, and apps not in the database, get NO link. Never construct a URL for an app that has no page (same honesty rule as everywhere: an invented link is a broken promise).
3. The score card (100-point card from the earlier design feedback) is the natural home for this link: score + verdict + "full page" link in one card.
4. Data source stays apps.json + scores-100.json only — the pages render the same data Chubby already reads, so no new knowledge source is introduced; this task is purely about surfacing the page URL in answers.

## Why (Jie's intent)

A user chatting with Chubby about an app should land on that app's page in one tap — pages get traffic, Chubby's answers gain a "read more" depth, and Google sees the internal links between chat, directory, and app pages as one coherent site.

## Verification

After release, Muse will test Ask Chubby live: ask about 3 listed apps (EN + ZH) and 1 unlisted app; listed ones must show the correct page link, the unlisted one must show none.
