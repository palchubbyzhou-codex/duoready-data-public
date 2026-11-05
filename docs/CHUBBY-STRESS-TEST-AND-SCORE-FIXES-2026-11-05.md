# Ask Chubby stress test + editorial score fixes — 2026-11-05

For: Codex (site/chat changes). Data fixes below are already done and live; the chat/site items are findings only — no site code was touched.

中文摘要：数据侧 10 处打分已按 rubric 修正并上线（双仓 + scores-100 已同步、线上端点已验证）。Ask Chubby 压测 14 题：零编造守住了（原神帧率、TikTok 诱导、Spotify 都没乱说），但有 2 个 P0：① 问不存在的 App「Floopr」却返回抖音的卡片；② 网站聊天里抖音/小红书的介绍文字与数据库 apps.json 对不上（抖音站内文字是吹「全新交互」的旧稿，数据库核实结论是未适配/黑边）——分数一致、文字漂移，需要单一数据源。另外目录/App 页根本不显示分数（只有聊天卡和 Outlook 精选页有）。

---

## Part 1 — Score fixes APPLIED to apps.json (live 2026-11-05)

Method: every listed app's `editorial_score` re-derived from its own record's cited evidence under the rubric in `data/SCHEMA.md`. Only clear contradictions changed. Private commit `11fdad2`, mirror commit `caaa7ed`; scores-100.json regenerated in the same round (distribution now 100:36 / 80:60 / 60:100 / 40:3 / 20:1); live raw endpoints verified.

| slug | old → new | reason (record's own evidence) |
|---|---|---|
| detail | 5 → 4 | Video + transcript side by side is a two-pane layout = rubric 4. Core AI on-device is not a Duo feature. |
| penbook | 5 → 4 | Two-page spread is a layout; "support for Duo poses" names no specific beyond-layout feature. |
| amap | 5 → 4 | Split-screen navigation is *announced* (将上线）, not shipped. Shipped evidence = two-pane layouts. Revisit when it ships. |
| callsheet | 5 → 3 | Release notes document "support" + multi-instance only; no Duo layout or Duo-specific behavior documented. |
| planet-of-lana | 4 → 3 | Record itself states "No specific split or cover-screen layout was described." |
| retrocade | 4 → 3 | Evidence is App Store collection boilerplate only; same evidence class as crossy-road (3). |
| sneaky-sasquatch | 4 → 3 | Same as retrocade. |
| instagram | 4 → 3 | "More posts and Stories onscreen at once" describes no layout; same class as shop / salesforce (3). |
| bear-us | 3 → 4 | Same app, same Fits Duo evidence as bear-cn (4): panel layout fills inner display, adapts on fold. |
| rednote | 4 → 5 | Video notes keep playing on the OUTER screen when closed (cover-screen behavior = rubric 5) + half-fold desk mode + two-pane notes. Same pattern as netflix (5). |

Checked and deliberately NOT changed:
- wechat = 2 is correct (two-pane exists, but black bar remains, old SDK tier, no tablet mode — textbook rubric 2).
- outlook = 3 stays (fills screen; the headline two-pane has not shipped — move to 4 when it does).
- Borderline, left for a possible stricter pass: vllo / pga-tour / paramount-plus / notewise / airmail / united at 4 on thin Apple one-liners; night-sky / portal / tide-guide / feishu / mindnode at 5 on thin-but-defensible Duo-specific claims.
- No listed app was missing a score in the data (all 200 records carry one). Missing scores are a *display* issue — see Part 2, item 6.

## Part 2 — Ask Chubby stress test (live site, 2026-11-05 08:23–08:29 ET, 14 questions)

Held the line (no fabrication): Genshin 120 fps → honest no-match; TikTok "special split-screen mode" bait → not confirmed; Spotify → "unconfirmed, not ruled out"; WeChat answer accurate incl. transitional caveats; Netflix score card correct (100/100).

### P0 — wrong-app match
Asking about a nonexistent app, **"Floopr"**, returned Douyin's score card and full answer verbatim (identical to the Douyin question). A made-up name must fall through to the no-match path, never to another app's record.

### P0 — chat text drifts from the database of record
Scores shown in chat match scores-100 (×20), but the adaptation text/sources for at least two apps do not match `apps.json`:
- **Douyin**: chat quotes a 2026-10-22 风云科技视 piece hyping Douyin 34.0.0's "folded Duo" interactions. The database record (verified 2026-10-28, hands-on sources) concludes Douyin is **not adapted** — centered phone-ratio window, black bars both sides. The chat text materially contradicts the verified record while displaying its 20/100 Poor card.
- **RedNote**: chat quotes an IT之家 9.52 piece （双列/半折分屏）; the database record cites 极客公园 hands-on (image/text split, outer-screen video continuation). Different source, different facts.
- WeChat's chat text matches apps.json verbatim, so the chat layer is only *partially* synced. Fix direction: chat + app pages should read the runtime JSONs (apps.json / scores-100.json) as the single source of truth — no site-side copies of adaptation text.

### P1 — self-contradictory answer template
Answers that contain a full sourced score card are prefixed with **"I'm not sure about this one yet."** (WeChat, Douyin, Floopr/Douyin, and both Chinese questions). The uncertainty prefix should only fire on the genuine no-match path.

### P1 — intent routing gaps (the original buyer-question failures, still open)
- "What case should I buy for my iPhone Duo?" → returned the stock snapshot (same as the buy question). "Case" is routed to stock; kits/accessory data is never surfaced.
- "Where can I buy the iPhone Duo and how much does it cost?" → stock snapshot only; no price, no retailers.
- "Which apps have the highest score on DuoReady?" → deflects ("What is the exact app name? Which store…") instead of answering from scores-100 data.

### P2 — recommendation quality
- "Which app lets me watch a video and chat at the same time?" → generic social candidates (Facebook / Instagram / JusTalk) with no scores and no direct answer; the documented watch-and-chat app (Feishu, CN record) is never surfaced (US-records-only restriction?).
- "Recommend a music app" → candidate list only, no scores shown.

### P2 — language matching
Chinese questions （微信/小红书） get a Chinese card but the opener string stays English ("I'm not sure about this one yet."). Localize the template strings with the card.

### P2 — scores are not displayed outside chat
- Directory list and app popups show only an "Adapted" badge — no numeric score (checked Netflix, Bear).
- The RedNote app page (/en/apps/rednote/) shows no score either; the 80/100 exists only in chat.
- Only the Outlook spotlight page renders a score ("DUOREADY SCORE 60/100 · 3/5").
- If scores are meant to be public, render them from scores-100.json on directory cards + app pages.

### P2 — naming inconsistency
Homepage hero says "iPhone Fold"; chat and directory say "iPhone Duo".

---
Data side is closed. Chat/site items above are Codex's queue, in priority order.
