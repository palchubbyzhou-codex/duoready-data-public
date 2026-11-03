# OPEN WORK ORDERS — 未完成工作单总索引

**给 Codex 的用法**：这是本仓唯一的待办入口。每次开工先读本页，按优先级逐项施工；每完成一项，把该项状态改为 ✅ 已完成 + 日期，并注明验收方式。施工细节都在每项的来源文档里（同在 docs/）。
**分工**：网站与 Ask Chubby 对话逻辑 = Codex；数据库与来源核实 = 助手（Muse）。运行时数据文件（apps.json / kits.json / news.json / basic-chat.json 等）只走每日数据管道，**不要手改**。
最后更新：2026-11-03（助手）

## 未完成

| # | 工作单 | 来源文档 | 状态 |
|---|--------|----------|------|
| 1 | **轻页缺失**：10 个已上架 App 无轻页（outlook、antiqsnap、fantastical-calendar、genk-cn、ima-cn、instagram-edits、things-3、ticktick-us、tips-tricks-pro、xinguang-cn），全量重跑生成器 + 部署；另清理 3 个旧 slug 僵尸页（edits、fantastical、things）；sitemap 计数须与 listed 数对齐 | HANDOFF-CODEX-2026-10-31-LIGHTPAGES.md | ⏳ 待施工（助手部署后逐个验 200） |
| 2 | **Ask Chubby 第 2 轮压测修复**（P0 意图门：问句不许整句当应用名复述；P0 规格卡：数据已由助手核实备好，在报告内；P0 概念答：未适配会怎样/是否所有 App 都能用/分屏；P1 库存意图扩词、模糊匹配置信门槛、抖音答全、隐私统一拒绝、站点身份意图；P2 限流与商店自动切换明示） | STRESS-TEST-ASK-CHUBBY-ROUND2-2026-10-31.md | ⏳ 待施工（修完助手按报告"复测队列"原样复测） |
| 3 | **网站视频模块**施工（Duo News / 视频区） | HANDOFF-CODEX-2026-10-30-VIDEO-MODULE.md | ⏳ 待施工（完工后助手上站验收） |
| 4 | **抖音循环事故**后续确认：第 2 轮压测中抖音问答行为正常（CN 限定、无循环），请确认事故修复已上线后关闭本项 | ASK-CHUBBY-LIVE-ISSUE-2026-10-28-DOUYIN-LOOP.md | 🔍 待确认关闭 |
| 5 | 小瑕疵：问 Outlook 时评分卡曾显示 "Not scored"（Outlook 实际有 60/100），顺手修 | 本页记录（2026-10-31） | ⏳ 待修 |
| 6 | **库存 SEO 页面矩阵 Phase 1**：/stock/ 枢纽页 + 州页 + 254 个门店页，数据用公开仓根目录 stores.json（每日管道再生）；抄 InStock Radar 的 SEO 打法、内容全用真实掉货数据；红线：无数据不许编、TBD 型号不许猜名 | HANDOFF-CODEX-2026-11-02-STOCK-SEO-MATRIX.md | ⏳ 待施工（完工后助手按单内验收清单抽查） |
| 7 | **主页 Tracker 面板换 C+B 组合**：平时=最近验证掉货卡+验证章+三数；验证进行时整块翻成深色大字报（数据走直播同份 verify.json/verify-stats.json，无通路先停下报告、不许写死假数） | HANDOFF-CODEX-2026-11-01-TRACKER-PANEL.md | ⏳ 待施工（2026-11-01 已交单；完工后助手上站验收） |
| 8 | **网站文案 10 分钟 → 5 分钟**：轮询已于 2026-11-02 加密为 5 分钟一轮；现行首页三处（Hero「Every 10 minutes」/「SWEEP = 10-MIN SCAN」/Tracker「refreshes every 10 min」）改 5 分钟口径，新版首页同口径、不许把 10 分钟带上线 | HANDOFF-CODEX-2026-11-02-STOCK-SEO-MATRIX.md（ADDENDUM 段） | ⏳ 待施工（并入今晚 SEO 同一轮；完工后助手上站验收） |
| 10 | **退回工单（2026-11-03 验收）**：FB-1「10 分钟」文案首页+/stock/ 共 8 处仍在（=#8/#9，两次验收未过）；FB-2 门店页把 "Availability temporarily unconfirmed" 当正式状态渲染；FB-3 卡片 112px 固定行高根因未改；FB-4 门店矩阵仅 10/254；FB-5 试点页缺 FAQ/验证数据/高峰窗/邻店内链；FB-6 配置清单与补货计数口径不一。数据对账、favicon、页脚日期等已验 OK 项列在单内，勿重做 | HANDOFF-CODEX-2026-11-03-FIXBACK.md | ⏳ 待施工（完工后助手按单内验收标准复验） |

## 参考（非工作单，施工前值得读）

- 真人试用原始记录：TRIAL-ASK-CHUBBY-2026-10-31.md（同事 5 问逐字 + 截图说明）
- 第 1 轮压测与修复对照：ask-chubby-stress-test-2026-10-28.md（第 2 轮回归 40/45 通过，未过项已并入工作单 #2）
- 战略共识：OPINION-CODEX-2026-10-30-STRATEGY.md（投稿试点、信任三分法、Chubby 双线）

## 已完成（近期）

- ✅ Favicon 全套部署（2026-10-31 助手验 /favicon.ico = 200）
- ✅ Ask Chubby 第 1 轮 22 项问题修复（2026-10-31 第 2 轮回归验证：追问上下文、名人 App 诚实答、隐私拒绝、新闻过滤、CN 错字澄清等均已过）
- ✅ Spotlight 第 1 篇 Outlook 上线

- **#9 (2026-11-02) New-homepage mobile fixes** — P0 directory card status clipped by fixed 112px grid rows vs 147px mobile cards; P0 pagination dead space on mobile; P1 'every 10 min' copy + panel cadence (= #8, still open); P1 sticky nav covers content; P2 footer date + loading states. Plus P1-7: tracker panel dark-mode palette clash / hollow left panel (Jie screenshot in docs/). Full brief: docs/HANDOFF-CODEX-2026-11-02-MOBILE-FIXES.md
