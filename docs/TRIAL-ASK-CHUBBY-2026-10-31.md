# Ask Chubby 真人试用报告 — 第 1 批（2026-10-31）

实验：Codex 定版的本周唯一动作。无引导，试用人用自己的真实问题问 getduoready.com 的 Ask Chubby。
试用人：Jie 的 2 位同事（工作现场，Jie 本人转交截图）。目标 3 人，已完成 2 人。
截图存档：your_files/ask-chubby-trial-2026-10-31/shot1–shot4（本报告引文与截图逐字一致）。

## 结果总览：5 问，0 解决

按 Codex 判定口径（真问题被解决且用户认可才算数）：**0 / 5**。
但诚实底线守住了：Chubby 没有编造任何未核实信息。问题不在诚信，在**意图路由**——真人不会像测试题那样提问。

## 逐字记录

### 试用人 A（塔台工作站，截图 shot1）
- **Q1**（问题被滚动遮住，仅见回答尾部，是一个 App 适配类问题）
  A：「I'm not sure about this one yet. …evidence for it yet. That means "not confirmed," not "not supported." If you have its App Store link, send it through Feedback and the maintainer can verify it.」
- **Q2**：「Can I order the Duo right now?」
  A：「I haven't matched that one yet. I don't have a sourced answer to this factual question. I cover Duo apps, stock and related news.」
  → **失败类 B**：这正是库存追踪的本职问题（欢迎屏甚至有 "Check stock" 入口），自由文本却没有路由到库存数据。

### 试用人 B（笔记本，截图 shot2–shot4）
- **Q3**：「are iphone programs rescaled for the iphone duo?」
  A：「I checked "iphone programs rescaled" in the US directory, but I don't have source-backed Duo support evidence for it yet. That means "not confirmed," not "not supported." …」
  → **失败类 A + C**：整句问题被当成 App 名查库；而且"rescale"就是本站的核心概念（适配），这是全站第一概念问题，居然无答。
- **Q4**：「what case is best for the duo?」
  A：「I haven't matched that one yet. I don't have a sourced answer to this factual question. I cover Duo apps, stock and related news.」
  → **失败类 B（更正 2026-10-31 15:45）**：配件问题。原报告称"kits 数据可查"有误——kits.json 是按身份分的 App 套装（学生/骑手/创作者等），不是手机壳配件库；配件目前**无任何数据源**，属纯覆盖缺口，正确行为只能是诚实未覆盖（说辞仍可改进）。
- **Q5**：「whats the frame rate on the Duo」
  A：「I checked "whats frame rate" in the US directory, but I don't have source-backed Duo support evidence for it yet. …」
  → **失败类 A**：设备规格问题被整句当 App 名查库。把用户原话整句当"应用名"念出来，是观感最差的一处——第一眼就像坏了。

## 失败分类（给 Codex 的修复清单）

- **A 意图误判**：带疑问词/问句结构（what/can/are/best…）的输入不应进 App 名查库。建议：意图门先进，App 查库只接"像名字"的短查询。
- **B 能力闲置**：库存（stock 数据现成）、配件（kits.json 现成）都有数据源，只差路由。建议意图处理器：order/buy/in stock → 库存现状回答 + 追踪页链接；case/cover/accessory → 查 kits 并带核实等级呈现。
- **C 概念无答**：rescale/adapt/怎么工作类问题 → 一段有出处的概念解释 + 按分类浏览目录的入口。这是新用户最可能问的第一问。
- **D 模板观感**：未命中时不要把整句原话当应用名复述；改为亮出 Chubby 真正能做的 3 件事（查 App 适配 / 看实时库存 / 推荐同类 App）让用户点。

## 数据侧（助手）待办

1. 从苹果官网核实 Duo 显示规格（刷新率等），整理成有出处的事实条供 Codex 做规格意图卡——核实前不写任何数字。
2. kits.json 对 case 类查询的覆盖自查，结果附到下一轮交接。
3. 若要给 Chubby 喂"当前库存一句话摘要"，涉及 basic-chat.json 字段——按规矩先与 Codex 协调，不擅自改。

## 下一步

- 本报告双仓存档，供 Codex 修对话层（意图路由归 Codex，数据与核实归助手）。
- 还差第 3 位试用人（目标 3 人）；修完后用本批 5 问 + 原 44 题一起复测。
