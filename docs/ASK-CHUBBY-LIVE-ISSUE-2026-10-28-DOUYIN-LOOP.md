# Ask Chubby live issue — Douyin question falls into a fallback loop (2026-10-28)

Reported by Jie from a live session on getduoready.com, 2026-10-28. Verbatim flow:

1. User: 「你知道抖音适配了吗」
   Chubby: no sourced data for Douyin; not covered ≠ not supported; offers App Store link for maintainer verification. (Honest — but see data fix below.)
2. Follow-up: Chubby generic no-match reply + chips: 推荐笔记 App / 微信适配了吗？/ 查看库存.
3. Next: the "by job" kit fallback fires (Penbook list) — unrelated to Douyin.
4. Next: the SAME kit fallback text repeats verbatim. Chips keep recycling 推荐笔记 App.

## Data side — FIXED by the assistant (2026-10-28)
Douyin （抖音） was missing from the database — a real gap for CN users. It is now in apps.json:
- slug `douyin`, store CN, category video, **status `not_adapted`** (NEW status value; SCHEMA anticipates future values with a source)
- editorial_score 1 (score_100 = 20) — rubric reading: no evidence of a real Duo layout; hands-on tests show a letterboxed phone window with black bars on both sides
- credibility_tier `reported` — Sina coverage of hands-on tests (incl. He Tongxue's 25-app test), source_url in the record
- listed_on_site = false (Jie publishes)
Expected behavior now: a direct Douyin question should hit this record and answer "not adapted yet" WITH the source — not "not covered", and not the kit fallback.

## Conversation side — for Codex (live reproduction of stress-test P0 #1/#2)
- After an honest miss, follow-ups degrade into the generic kit fallback, then the fallback REPEATS verbatim — the user experiences this as "一直循环" (looping).
- Suggestion chips recycle the same unrelated items （推荐笔记 App） regardless of context.
- Asks: (a) never emit the identical fallback text twice in a row in one session; (b) when a named app exists in the DB (now including not_adapted records), direct lookup must win over the kit fallback; (c) chips should follow the current topic or disappear, not loop.
