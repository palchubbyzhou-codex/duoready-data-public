# DuoReady Spotlight — fixed format for featured app reviews

**Series name (settled by Jie + Codex):** EN "DuoReady Spotlight" · ZH: DuoReady 特写 (settled by Jie 2026-10-29)
**First feature:** Microsoft Outlook (package in `features/spotlight/outlook/`)

Every Spotlight feature follows the SAME fixed structure, in this order. Readers should recognize the format at a glance; only the facts change.

## Fixed structure (both languages, separate files, never mixed)

1. **Title** — the honest question or verdict, never clickbait beyond what the sources prove.
2. **Header block** — series name + feature number, score (5-point AND 100-point), status word, "sources verified" date.
3. **One-line summary （一句话总结）** — the whole verdict in 2–3 sentences, plus one analogy a non-technical reader gets instantly (Outlook used the folded-newspaper analogy).
4. **What you get today （现在已经有的）** — only shipped, sourced facts. Each bullet traceable to a named source.
5. **What's still missing （还缺的）** — promised-but-not-shipped features, undocumented areas, discoverability gaps. Stated as plainly as section 4.
6. **Slab vs. Duo comparison （对比）** — table + the original schematic illustration (today / coming states visually separated). The illustration is ALWAYS labeled as an illustration based on official statements, never presented as a screenshot.
7. **Verdict （结论）** — score restated with the reasoning in one paragraph, plus the re-check commitment: when the missing piece ships and is confirmed, the feature is re-tested and re-scored.
8. **What to watch （接下来盯什么）** — the specific next signal (a version number, a release-note phrase) that would change the verdict.
9. **Sources** — full list with URLs. Mandatory, no exceptions.

## Rules

- Score = editorial 5-point × 20. credibility_tier stays separate, never merged into the score.
- No claim without a source; "reported" and "verified" are never blurred. Absence of hands-on evidence is itself stated when true.
- Images: official product imagery or original DuoReady illustrations only; third-party usage photos, if ever used, carry creator credit + source link on the page.
- One feature = one app. Cadence is quality-gated, not calendar-gated.

## Site section （入口） — for Codex to build with the first feature

- Homepage + directory top: a Spotlight section card — app icon, one-line verdict, score; tap → the feature page. Rotates to the newest feature.
- Directory rows: featured apps carry a "Spotlight" marker; tapping it goes to the feature page (not the light page).
- Feature pages cross-link at the bottom ("More Spotlight features").
- Suggested routes: `/spotlight/<slug>/` (ZH default) + `/en/spotlight/<slug>/`, added to the sitemap.
