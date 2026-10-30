# Verification report: per-app pages + Ask Chubby page links (2026-10-29)

Verified live by Muse after Codex's build, against BRIEF-PER-APP-PAGES-2026-10-29 and its Ask Chubby addendum.

## Per-app pages — PASS

- Sitemap: 28 → 252 URLs. All 121 `listed_on_site: true` apps have pages; **zero** pages for the 16 unlisted apps (red line held).
- New-template pages spot-checked (Airmail EN/ZH): question-style title with score_100, 5-point score shown, source named, Ask Chubby CTA present. Rendered from apps.json data as specified.
- DB-slug URLs resolve for all three legacy-slug apps (things-3, fantastical-calendar, instagram-edits all return 200).

### Minor nits (non-blocking)
1. Sitemap lists legacy slugs (things, fantastical, edits) instead of the canonical DB slugs. Both resolve; canonicalizing the sitemap entries would be cleaner for SEO.
2. The 9 legacy hand-made pages keep their old template (no question-title/score-in-title). Acceptable, noted for consistency.
3. No /zh/apps/<slug>/ routes — ZH app pages live at the default route, matching the site's pre-existing convention. Accepted.

## Ask Chubby page links — ONE DEFECT TO FIX

Live tests (same session, 2026-10-29):

| Test | App | Score card | Page link |
|---|---|---|---|
| EN, US store | Airmail (listed) | ✅ 80/100 | ❌ **"View record" links to the directory search anchor `/?market=us&q=Airmail#directory`, NOT to `/apps/airmail/`** |
| ZH, CN store | QQ音乐 (listed) | ✅ 60/100 | ✅ "查看记录" links to `/apps/qq-music/` |
| ZH, CN store | 微信 (in DB, NOT listed) | ✅ 40/100 | ✅ Correctly NO app-page link (directory query only) |

**Fix required:** the US-store (and default-market) record link must point to the app's own page `/apps/<slug>/`, exactly as the CN-store one already does. The behavior is currently inconsistent by market.

Minor: the link label is "View record / 查看记录" rather than the addendum's suggested "Full adaptation page / 查看完整适配页" — acceptable, but the fuller label describes the destination better. Also, the CN answer header said "I'm not sure about this one yet" despite a sourced record existing; the cautious template reads as uncertainty where we actually have data.

Positives confirmed: no loops, no repeated fallback answers, score card shows the linear-rescale methodology note, and unlisted apps get detailed honest answers with no fabricated page links.
