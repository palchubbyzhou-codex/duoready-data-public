# DuoReady Adaptation Index（适配指数）— 方法论与上线交接

Jie 2026-11-12 拍板：双榜 Top 100 口径。Codex 按此上线到 getduoready.com 首页面板 + /adaptation-index 页。

## 口径（写死，不许改）

- **分母**：App Store 官方免费榜 Top 100，共四榜——美区应用、美区游戏、国区应用、国区游戏（共 400）。榜单来自 Apple 官方 charts（rss.applemarketingtools.com / iTunes RSS），名单公开、人人可复核。
- **分子（已确认适配）**：只数有公开证据的适配，满足其一即算：
  1. 已收录 DuoReady 核实目录（data/apps.json，status=adapted）；
  2. App Store 当前版本更新说明或 App 介绍中明确写明适配 iPhone Duo（如 "added support for iPhone Duo"、「适配 iPhone Duo / 折叠屏」）。
- **未确认 ≠ 未适配**：没公开宣布的，哪怕实际能铺满屏，也先算「未确认」。页面文案必须保留这一句口径说明，不许把数字包装成「实际适配率」。
- 百分比 = 已确认 / 100（分榜）与 / 400（综合），保留一位小数。

## 基线（2026-11-12，首测）

| 榜单 | 已确认 | 比例 |
|---|---|---|
| 美区 Top 100 应用 | 13 | 13.0% |
| 美区 Top 100 游戏 | 0 | 0.0% |
| 国区 Top 100 应用 | 24 | 24.0% |
| 国区 Top 100 游戏 | 2 | 2.0% |
| **综合** | **39 / 400** | **9.8%** |

- 明细：`baseline-2026-11-12.json`（每榜 100 条：排名、trackId、名称、版本、状态、证据来源）。
- 已知口径效应（预期内、不是 bug）：美区大厂多为「静默适配」（靠新 SDK 铺满屏、不写进商店文案），如 ChatGPT、TikTok、WhatsApp 实际已适配但无公开声明，首测不计入；国区厂商习惯把适配写进更新说明，故国区数字显著更高。上线文案不要回避这一点——它本身就是故事（「国区厂商更愿意公开宣布」）。
- 对手参照：WorksOnDuo 用真机实测口径报美区 Top 100 应用 41% / 游戏 19%（Macworld 2026-11-10 引用）；Duo Tracker 用全目录口径报 3.6%。我们的差异点 = 双区 + 分母公开 + 每日更新。

## 日更流程（并入现有日更管线，不另起炉灶）

1. 每日拉四榜 Top 100（charts 接口见下），与昨日名单 diff（新进榜的要补核）。
2. 对 400 个 trackId 批量 lookup（itunes.apple.com/lookup，country=us/cn），扫 releaseNotes + description 的 Duo 证据词（词表见基线脚本口径：iphone duo / 适配…duo / 折叠屏 / foldable / optimized for duo 等，防 duo mode 类误报）。
3. 与 data/apps.json 名称索引交叉（name_en/name_zh/aliases，去副标题归一化）。
4. 重算四榜 + 综合百分比，存当日 baseline；首页面板与 /adaptation-index 页读最新值，并保留历史序列画趋势线（上线第二周起有意义）。

## 上线形态

- 首页：效果图 `panel-mockup.png` 的面板（大综合数 + 四榜卡片 + 口径说明一行）。
- 独立页 /adaptation-index：四榜完整名单（排名 + 状态 + 证据链接），这是 SEO 与被引用面。
- 运行时数据文件（如 adaptation-index.json）如需新增，走日更管线生成——**不许手改公开仓的运行时 JSON**；本交接只加 features/ 文档与基线快照。

## 文件清单（本包）

- METHODOLOGY.md（本文）
- baseline-2026-11-12.json / summary-2026-11-12.json
- chart-us_apps.json / chart-us_games.json / chart-cn_apps.json / chart-cn_games.json（当日四榜原始名单）
- panel-mockup.html / panel-mockup.png（效果图源文件与成品）
