# HANDOFF — Codex 施工单 2026-11-04（修订版）：首页 Tracker 面板改造——订阅与提醒（工作单 #11）

**范围（Jie 2026-11-04 亲自收窄）**：只改首页中间那块 Tracker 面板（现标题 "iPhone Duo. Stock at a glance." 那一整块，含左侧状态区与右侧验证卡）。新闻相关的改动**全部取消**（新闻 Jie 已自行修好，不要碰）。直播端已由助手上线（每天 8:15–13:15 ET 自动开关播、大屏警报、Telegram 机器人自动发帖），不归 Codex。

这块面板现在的问题：只有「看」，没有「订」。用户看完就走，掉货不会找他。本单的目标是把它改成**订阅入口**：用户在这块里完成订阅，之后的掉货提醒自动找到他。

效果图：`docs/MOCKUPS-2026-11-04/tracker-2.0-mockup.png`（版式与文案口径为定稿方向；图中的门店数 269 是助手的笔误，**正确数字是 254**，一切数字以 stores.json / API 实时数据为准）。

## T-1 状态句（替换现左侧的 "No stock in the latest snapshot" + "Awaiting update"）

一行事实句，任何时刻都成立，数据走 /api/snapshot.json + /api/verify.json 实时拼装：
- 有货时：`{N} stores have it now · Last drop {time ET} · {store}`
- 无货时：`Sold out everywhere right now — drops cluster 9 AM–12 PM ET · Last drop {time ET} · {store}`
红线：不许再渲染 "Data temporarily unconfirmed"、"Awaiting update" 这类故障/等待文案作为常驻状态（API 健康时出现即验收不过）。

## T-2 订阅模块（本单核心：用户怎么订阅、订完怎么提醒他）

面板内新增订阅区，两种订法并排：

**A. Telegram 订阅（已通，订了立刻生效）**
- 按钮文案：`Get alerts on Telegram`，链 https://t.me/DuoReadyAlerts （新窗口）。
- 机制说明（给 Codex 理解，不要原样上页面）：频道由助手侧机器人自动发帖，两段式——掉货先发 `SPOTTED（未验证）`，验证器复核苹果后发结论帖 `✓ VERIFIED（附预订入口）` 或 `✗ SOLD OUT（别白跑）`。用户点按钮进频道点 Join 即完成订阅，站端不需要任何对接。

**B. 邮箱订阅（Codex 建收集，发送由助手侧接）**
- 表单：邮箱输入框 + 按钮 `Email me alerts`。只收邮箱一个字段（v1 不要门店偏好，降低门槛）。
- 提交必须**真落盘**：存站端可导出 CSV 的存储（表至少含 email、subscribed_at、source=homepage-panel）。重复订阅返回「已在名单上」状态，不许重复入库。
- 成功态文案（定稿）：`You're on the list. The next verified drop lands in your inbox — spotted first, then verified, so you never make a wasted trip.`
- 失败态要有明确提示。隐私小字一行：`Alerts only. No spam. Unsubscribe in every email.`
- **分工**：Codex 只负责收集 + 落盘 + 可导出（CSV 下载或只读接口，形式自选但要写进完工报告）。提醒邮件的实际发送由助手侧用导出的名单接线，Codex 不要自建发信系统。

## T-3 节目与档期信息（替换现 "Live 24/7" 文案）

现面板左上写着 `Live 24/7 · refreshes every 5 min`——直播已不是 24/7，此文案必须改：
- 改为：`Tracker checks every 5 min · Live show daily 8:15 AM–1:15 PM ET`
- 加一枚节目 chip：直播时段内显示 `🔴 PEAK WINDOW LIVE`（链 YouTube 频道 @DuoReady），时段外显示 `Peak Window Live returns 8:15 AM ET`。时段判定用美东时间，可走 /api/chance-index.json 的现成字段或前端按 ET 计算（Codex 自选，须与实际档期一致）。
- Chance Index 可选项：若版式放得下，在节目 chip 旁显示当前 Chance Index 值 + 档位词（ICE COLD / COLD / FAIR / WARM / HOT，与大屏口径一致），放不下可省。

## T-4 验证带（保留，不许改口径）

右侧验证卡（LATEST APPLE VERIFICATION：店名 + VERIFIED / SOLD OUT 章 + 验证时间）与三数（DROPS TODAY / VERIFIED AT APPLE / FASTEST GONE）**保持现状**，数据继续走 verify.json / verify-stats.json。这是全站唯一已验好的部分，只许跟着新版式微调样式，不许改数据口径。

## T-5 按钮区

保留 `Open full Tracker`；新增 `Watch live`（链 YouTube @DuoReady 直播）；Telegram 按钮在 T-2 订阅区内，不在此重复。

## 验收（助手执行）

- 按效果图逐块对照；T-1 状态句与 API 实时数据逐字对账（有货/无货各验一次），页面停留 60 秒不得出现故障文案。
- T-2：点 Telegram 按钮进频道无误；用测试邮箱实测提交，确认落盘可查、成功态/重复态文案正确。
- T-3：档期文案与实际开关播时间一致（13:15 后验一次时段外状态）。
- 390×844 移动端截图：面板无溢出、订阅表单可完整操作。

## 分工红线

不要动新闻任何页面；不要动服务器、直播、Telegram；不要手改运行时数据 JSON；不要改 Ask Chubby。拿不准先停下留言，不要编数据。

## T-6（Jie 2026-11-04 追加）双死状态的展示规则：没货时、下播时，面板重点展示「订阅」

面板最难看的时刻是「没货 + 已下播」——但这恰恰是常态（一天里大部分时间都无货，13:15 后节目还下播）。规则如下：

- **触发**：(a) 当前无货（验证后有货数为 0）；(b) 当前不在直播时段（13:15–次日 08:15 ET）。两者可叠加，权重按 (a)+(b) 累加。
- **无货时**：订阅区（T-2）视觉权重升为面板第一位——标题 `Don't watch a page. Get pinged.` + Telegram 按钮 + 邮箱框置顶；状态句（T-1）紧随其后；验证战绩带（T-4：今日掉货数 / 验证数 / 最快消失）保留展示。**无货 ≠ 没内容，战绩就是内容。**
- **下播时**：面板顶部加节目预告条：`Peak Window Live returns tomorrow 8:15 AM ET` + 一句今日战报（如 `Today: 14 drops, all verified. Fastest gone: 1 minute.`，数据走 verify-stats）；订阅区位置不变。
- **红线**：不许出现「下播了 / 关门了 / 回来再看」式文案让人以为 tracker 停了——**只有节目下播，数据 24/7 照常实时刷新**，面板数据区必须保持实时更新状态。
- **有货且直播中**：恢复常规权重（状态句第一、订阅区第二、节目 chip 显示 🔴 直播中）。
