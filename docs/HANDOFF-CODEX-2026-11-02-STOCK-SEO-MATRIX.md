# HANDOFF — Codex：库存 SEO 页面矩阵（门店页）

- 日期：2026-11-02
- 出单：Muse（助手）；Jie 已批准（2026-11-02：「开抄：先出 Codex 施工单（门店页矩阵）」）
- 背景：竞品 InStock Radar 靠「国家×型号×城市×门店」模板页矩阵（估 3,000–6,000 页）零广告费吃 Google 自然搜索。我们的数据比它硬（254 家美国 Apple Store 的真实补货历史 + 每条掉货经 Apple 官网复核），抄它的打法、页面内容全用真数据。情报依据：`~/workspace/duoready-watch/competitor-intel-instockradar-2026-11-02.md`（公开仓无此文件，向助手索取即可）。

## 数据（已备好，不要手改）

- **`stores.json`**（公开仓根目录，与 apps.json 同级；每日由数据管道从直播 tracker 的 history/snapshot 再生，字段结构以文件内 `meta` 为准）：
  - `meta`：generated_at_utc、stores_tracked=254、history_span、parts_legend（6 个型号，2 个已证实命名、4 个标 TBD——**TBD 就是 TBD，页面上照原样显示，绝不猜名**）。
  - `stores[]`：slug、store_number（R 号）、name、city、state、latitude/longitude、drops_last_7d（近 7 天补货次数）、last_drop_at_utc / last_drop_et、last_drop_models[]、peak_window{window_et, drops}（样本小则为 null）、fastest_gone_min（可配对观测的最快售罄分钟数，无则 null）。
- 若施工时公开仓根目录没有 stores.json → **停下报告，不要用假数据顶**。

## 本期范围（Phase 1）

1. **枢纽页 `/stock/`**：全国概览（追踪门店数、近 7 天补货总次数、最爱掉货门店 Top 10、州索引），并保留现有 tracker 入口/直播入口。页面须标注数据更新时间（stores.json 的 generated_at）与「每日更新」口径——这些页面不是实时页，不许写「实时」。
2. **州页 `/stock/{state 小写}/`**：该州全部在册门店列表（店名、城市、drops_last_7d、最近掉货时间），州汇总（门店数、7 天补货数），链回枢纽页。
3. **门店页 `/stock/store/{slug}/`**（254 页），每页至少包含：
   - H1：`iPhone Duo stock at Apple {name} — {city}, {state}` 一类直白标题；
   - 状态块：近 7 天补货次数、最近一次掉货（时间 ET + 型号原文）、peak_window（仅当 peak_window 非 null 且 drops ≥ 2 时显示，否则整段省略）、fastest_gone_min（非 null 才显示，措辞用「最快一次约 X 分钟售罄（观测）」）；
   - 「怎么抢」三步（与直播大屏 60-SECOND DRILL 同口径：提前在 Apple Store App 收藏本店+选好型号 → 掉货窗口蹲守 → 掉货后先下单自提再出门）；
   - 同州其他门店链接（按 drops_last_7d 降序取 6 家）+ 州页链接 + 枢纽页链接 + App 目录相关链接；
   - 零掉货的店同样建页，状态块如实写「近 7 天未记录到补货，最近一次：{last_drop_et 或 从未}」——**不许用模板空话填充**。
4. **SEO 基础**：每页独立 title / meta description（带店名与城市）、canonical 自指、全部新 URL 进 sitemap.xml；州页与门店页互相内链成网。

## 红线

- 只用 stores.json 里的数据。我们**没有**的数据（门店地址、营业时间、电话、评价）一律不许出现——不要从别处拼凑。
- 不改动任何现有运行时 JSON 的结构；stores.json 只读消费。
- 页面视觉沿用现站设计语言即可，不新起设计系统。

## 非目标（Phase 2，勿在本单施工）

城市页 `/stock/{state}/{city}/`、型号×门店页、中文版门店页。

## 验收（完工后助手执行）

- 抽查 Florida Mall 页（drops_last_7d=6）+ 任意零掉货店页 + 任意州页：数字与 stores.json 逐项一致；
- 三类页面 HTTP 200，sitemap 含全部新 URL 且计数对得上（254 门店页 + 州页数 = stores.json 中 distinct state 数）；
- 完工后把 OPEN-WORKORDERS 本项标 ✅ 并注明上线日期。

---

## ADDENDUM — 2026-11-02 下午：轮询已加密到 5 分钟，网站文案同步改（Jie 指令）

背景：2026-11-02 黄金窗口（9AM–12PM ET）全美只有个位数掉货且存活极短，我方 10 分钟轮询全数错过（对手 ISR 抓到 5 家）。轮询器已于当日改为 **5 分钟一轮**（服务器 duo-poller.timer，OnUnitActiveSec=5min，已生效）；Chance Index 计算同步改 5 分钟；直播大屏与 YouTube 简介已由助手改完。网站文案请 Codex 在今晚 SEO 施工同一轮里改掉以下三处（当前线上旧版首页实测原文）：

1. Hero：「Every store. Every 10 minutes. One sky.」→ 「Every store. Every 5 minutes. One sky.」
2. STAR SWEEP 条：「SWEEP = 10-MIN SCAN」→ 「SWEEP = 5-MIN SCAN」
3. Tracker 面板：「Live 24/7 · refreshes every 10 min」→ 「Live 24/7 · refreshes every 5 min」

新版首页（本地已批、待上线）如有同类字样，一律用 5 分钟口径，不要把 10 分钟带上线。红线同主单：文案只写真实频率，不许写比 5 分钟更快的数字。
