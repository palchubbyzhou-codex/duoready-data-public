# Data Update Note for Codex — 2026-10-28

Runtime data changed today in the public mirror (apps.json / news.json). No code change is needed — the site and Ask Chubby read these files at runtime. This note is so you're aware of what changed and why.

## Changed

**WeChat record (apps.json, slug `wechat`, CN) — refreshed and re-verified 2026-10-28.**
The 8.0.80 adaptation is now described in full, from hands-on reporting （新浪/IT之家， 2026-10-23):
- Unfolded: two-pane layout (conversation list left, chat detail right) — this was already in the record.
- **New detail:** half-folded, the chat stays on the top half and the input area on the bottom half, avoiding the crease.
- Still transitional: older SDK tier, black bar remains along the right side, **no tablet mode yet** — the Duo is still recognized as a regular phone. Tencent says optimization will continue.
- Editorial score unchanged (2/5) — the state did not improve enough to re-score.
- Highlights updated to match (3 items).

**News (news.json) — one item added:** `2026-10-24-wechat-simultaneous-login-duo` — WeChat remotely switched on "log in together with other devices" for some Duo units (gradual rollout; prompts an iPad WeChat login; not full tablet mode). Source: IT之家 via 新浪财经， tier `reported`. News count is now 100.

## Not changed

- The other six records from this week's watch (apple-support, sonos, soldial, vibeshort, gospel-library, flipcorder) were re-checked and are current as of their 2026-10-27 verification — no edits.
- **No `listed_on_site` flags were touched.** Six records (wechat, apple-support, sonos, soldial, vibeshort, gospel-library) still carry `listed_on_site: false` in the data. Publishing to the directory remains Jie's action; the data is ready when he is.

## Why WeChat got the attention

Per Jie: WeChat is the one app Chinese users cannot avoid, so its record must never go stale. Expect its adaptation state to move again (tablet mode is the milestone to watch); data updates will keep coming through the daily pipeline.
