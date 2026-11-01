# Handoff for Codex — Replace the STAR SWEEP panel with the C+B verification panel

Prepared by Muse, 2026-11-01. Jie picked the C+B combo from three mockups the same evening.
Visual targets (in this repo, docs/TRACKER-PANEL-2026-11-01/):
- state-c-default.png — the idle state (light panel)
- state-b-verifying.png — the live-verification state (dark big board)
Numbers/store names in the mockups are real samples from 2026-11-01, for layout reference only.

## The prompt (Jie pastes this to Codex)

把新版主页 stock tracker 模块右边的 STAR SWEEP 星图换掉，换成「记分牌 + 验证大字报」
的组合面板（视觉目标见公开仓 docs/TRACKER-PANEL-2026-11-01/ 两张图），规则如下：

1. 默认态（C，浅色）：上半是最近一次验证卡——店名、城市/州、掉货时间（ET）；
   已售罄盖红色斜章「SOLD OUT / ✓ VERIFIED ON APPLE」，仍有货则用绿色带
   「✓ IN STOCK — VERIFIED AT APPLE」。下半三个数：DROPS TODAY（今日掉货次数）、
   VERIFIED AT APPLE（今日验证次数）、FASTEST GONE（今日最快售罄）。
   章不能压住店名，店名该换行就换行。
2. 验证进行中（B，深色大字报）：一旦有掉货正在被验证，整个面板翻成大字报——
   巨大店名、巨大结论（有货=绿色 ✓ IN STOCK AT APPLE；售罄=红色 ✕ SOLD OUT）、
   「VERIFIED ON APPLE · 时间」，下方滚动验证日志（每次向 Apple 复查的时间+结果）。
   热门店（≥2 个型号有货，或存活满 5 分钟）加「🔥 HOT DROP — STILL AVAILABLE」
   条幅、结论呼吸闪烁——和 YouTube 直播大屏现行逻辑完全一致。验证一结束，自动翻回
   默认态 C，且 C 的「最近一次验证卡」就是刚刚这一单。
3. 数据通路先行：今日掉货数、今日验证数/最快售罄、最近一次与进行中的验证会话，
   都来自 tracker 服务器上的 verify.json / verify-stats.json / history.json
   （与直播大屏同一份数据）。网站若已有从该服务器拉 snapshot 的现成通路，沿用并
   扩展它；若没有，先停下来报告缺什么，不要用假数据或写死的数字占位。
   验证状态的刷新要跟得上直播感（建议 ≤60 秒轮询验证状态这一项），快照倒计时
   维持现有节奏。
4. 手机端：面板堆到左栏下方，大字报字号缩放不溢出，章不压字。
5. 不要动左栏文案、其他主页模块、apps/scores 的数据与显示逻辑，不要碰直播和服务器。
6. 发布后自检并回报：桌面+手机各一张截图；默认态与验证态各验一次（验证态可用
   一份样例 payload 模拟触发，但上线数据必须全真）；发现数据字段对不上先报告，
   不要编造。

## After Codex reports done

Muse verifies the live site (both states, desktop + mobile widths, numbers cross-checked
against the tracker server's verify-stats.json / history.json for that day) before Jie is
told it is live.
