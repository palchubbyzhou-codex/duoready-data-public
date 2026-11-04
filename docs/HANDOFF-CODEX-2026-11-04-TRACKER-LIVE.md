# HANDOFF — Codex 施工单 2026-11-04：Tracker 2.0 + Duo News 修复包（工作单 #11）

背景：2026-11-03 晚 Jie 与助手定版「直播改造」（高峰窗节目 + 免费提醒）。**直播端已由助手于 2026-11-04 上线，不归 Codex**：每天 8:15–13:15 ET 自动开关播、大屏掉货警报（闪烁+铃声混音进直播音频）、Telegram 频道与机器人两段式自动发帖。本单只含网站端四项。

已上线、Codex 直接引用的东西：
- Telegram 频道：https://t.me/DuoReadyAlerts （机器人自动发帖：SPOTTED → VERIFIED / SOLD OUT）
- 直播档期：每天 8:15 AM–1:15 PM ET（YouTube @DuoReady）；轮询器/验证器 24/7 不停
- 数据端点（不变）：/api/snapshot.json、/api/verify.json、/api/verify-stats.json、/api/chance-index.json；stores.json 在公开仓根目录（每日管道再生，勿手改）

## W-1（P0）首页 Tracker 区改版为 Tracker 2.0

效果图：`docs/MOCKUPS-2026-11-04/tracker-2.0-mockup.png`（图中数字为 2026-11-03 真实数据，版式与文案口径为定稿方向）。自上而下五块：

1. **状态句模块**（替代现 C+B 面板左半）：一行事实句，永远成立。有货时：`{N} stores have it now · Last drop {time ET} · {store}`；无货时：`Sold out everywhere right now — drops cluster 9 AM–12 PM ET · Last drop {time ET} · {store}`。数据走 snapshot + verify 实时拼装。**红线：任何状态下不许渲染 "Data temporarily unconfirmed" 类故障文案**（见 W-4）。
2. **提醒模块**（页面第一 CTA）：标题 `Don't watch a page. Get pinged.`；Telegram 按钮链 https://t.me/DuoReadyAlerts ；邮箱订阅位见 W-1.1。口径文案：two-step alerts（spotted → verified）、verified on Apple、no wasted trips。
3. **节目卡**：`Peak Window Live · Daily 8:15 AM – 1:15 PM ET` + Chance Index（/api/chance-index.json，档位词与直播大屏一致：ICE COLD / COLD / FAIR / WARM / HOT）；关播时段显示 `Back tomorrow 8:15 AM ET`。
4. **验证信任带**（保留现面板右半形态）：DROPS TODAY / VERIFIED AT APPLE / FASTEST GONE 三数 + 最新验证卡（店名 + VERIFIED 或 SOLD OUT 章 + 验证时间）。
5. **门店情报表 Top 5**：按 stores.json 近 7 天掉货数排序，列 drops（7d）、peak_window、fastest_gone_min；每行带 `Alert me`（→ Telegram 频道）与 `Store page →`（→ 对应门店页；门店页未上线的行链到 /stock/）。

### W-1.1（P1）邮箱订阅

输入框 + 订阅按钮；提交须落盘存储、可导出 CSV（方案 Codex 自选站端现成路子），成功态文案：`You're on the list. First alert hits your inbox at the next verified drop.` 重复订阅与失败都要有明确状态。**不许只做假按钮。**

## W-2（P0）/news/ 列表页 404

/news/ 与 /zh/news/ 现为 404。按 news.json 建索引页（标题、日期、摘要、封面位），与站内导航 News 入口对齐，中英双版。

## W-3（P1）新闻文章模板改真 HTML + iOS 27.3 文迁移

现 /news/ios-27-3-beta-1/ 的正文是 3 张 A4 文档图片（/assets/news/ios-273/page-5..7.png）：文字不可检索、不可选中、移动端需放大。把该文迁回**真 HTML 文本**，文章模板定为全站新闻通用。
版式三选一（效果图）：`docs/MOCKUPS-2026-11-04/news-a-dark-newsroom.png`、`news-b-broadsheet.png`、`news-c-special-report.png`。**Jie 圈选后按选定版式落地**；圈选前先做 W-1 / W-2 / W-4。模板组件清单（三种版式通用）：kicker、标题、导语、署名行（作者/日期/阅读时长/中文版链接）、正文（含首字下沉或等价处理）、数据组件（大数字条或 By the Numbers 框）、引文块、警示框（死线类信息）、来源小字。
旗舰篇《The Duo Was Never Supposed to Launch in October》（稿在公开仓 `duo-news/2026-11-02-first-piece/article.md`）上线时必须用新模板 + 真 HTML；配图仍等 Jie 的三张图（hero/zoom/ai-china），**缺图不许先发**。

## W-4（P0）FB-7：现面板左半故障文案驻留（并入 #10 追踪）

现 C+B 面板左半在 /api/snapshot.json 数据新鲜（stale=false）时仍渲染 "Data temporarily unconfirmed"（证据：2026-11-03 21:19 ET Jie 截图，助手同日 21:00 实测 API 为新鲜），与右半验证卡（更新至 21:18 ET）自相矛盾。修面板取数/新鲜度判定：故障文案只许作为 10 秒以内的客户端瞬时态出现，API 健康时不许驻留。若 W-1 先落地并替换该面板，W-1 状态句模块的验收通过即视为 W-4 关闭。

## 验收（助手执行）

- W-1：上线后按效果图逐块对照；状态句与 API 实时数据逐字对账（有货/无货各验一次）；390×844 移动端截图无溢出。
- W-1.1：实测提交一条测试邮箱，确认落盘可查、成功态文案正确。
- W-2：/news/ 与 /zh/news/ 均 200，条目与 news.json 一致。
- W-3：文章页 DOM 含正文文本（curl 可 grep 到正文句子），页面源码无 page-*.png 引用。
- W-4：API 健康时刷新页面停留 60 秒，故障文案不得出现。

## 分工红线

不要动服务器、直播、Telegram 机器人与频道；不要手改任何运行时数据 JSON；不要改 Ask Chubby 逻辑（#2 在办）。拿不准的数据口径先停下，在本单下留言，不要编。
