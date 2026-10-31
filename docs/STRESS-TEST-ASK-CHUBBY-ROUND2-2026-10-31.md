# Ask Chubby 压力测试 · 第 2 轮完整报告（2026-10-31）

**缘起**：Jie 的 2 位同事真人试用 5 问 0 解决（见 TRIAL-ASK-CHUBBY-2026-10-31）。本轮按 Jie 要求，沿同事的思维继续衍生、并加刁钻度，同时回归第 1 轮（2026-10-28）44 题验收脚本。

**方法**：getduoready.com 线上实测，Store US / Reply Auto 默认，6 个全新会话，逐字记录回复。评分：✅ 解决｜⚠️ 部分（诚实未解决）｜❌ 失败｜⏸ 被限流未测成。事实基准：apps.json 150 条（10/31 日更后）+ 苹果官网规格页。

**总成绩（84 条）**
| 批次 | ✅ | ⚠️ | ❌ | ⏸ |
|---|---|---|---|---|
| A 回归脚本（第 1 轮 44 题重构版，共 45） | 40 | 4 | 0 | 1 |
| B 衍生刁钻题（34） | 10 | 5 | 18 | 1 |
| 同事真人批（5，已单独成报） | 0 | 0 | 5 | 0 |
| **事实诚信（全部 84 条 + 全部施压题）** | **零编造** | | | |

## 一句话结论

**Chubby 已经学会了"考试科目"，但还没学会"真人说话"。** 第 1 轮的 22 个问题几乎全被 Codex 修好了——追问上下文、名人 App 诚实未覆盖、隐私明确拒绝、新闻过滤、角色套装、中文错字澄清，全部过关。但真人（同事）问的那类话——买、规格、壳、概念——仍然成片倒下：衍生题里"概念/规格/壳"整组 0/10。它的诚实是满分，路由是瘸的。

## 衍生逻辑（同事思维 → 刁钻题）

同事的 4 个问题代表 4 条真人思路，本轮沿每条往深处挖：
- 「能下单吗」→ 购买链：指定门店（Fifth Ave）、催它猜补货日期、让它代预订、问价格、问 512GB 值不值、问以旧换新
- 「程序会拉伸吗」→ 概念链：那是不是所有 App 都能用、没适配会怎样、能不能分屏
- 「什么壳好」→ 配件链：普通 iPhone 壳能不能凑合
- 「帧率多少」→ 规格链：换说法（refresh rate）、诱导二选一（就是 120Hz 对吧）、屏幕多大、电池多久
- 外加：查库刁钻（Netflix 有库题、outlok 错字、抖音≠TikTok 区分、卡车司机无套装角色）、施压（同事背书、二选一逼答、问 Jie 邮箱）、社交+查库混合题

## 关键发现

### 修好了（回归批 40/45，第 1 轮为 22/44）
- **P0 追问上下文**：`What about the China store?` / `And what's its score?` / `Why?` 三连全部接住微信上下文，分数 2/5 带解释带来源；中文 `那中国区呢` 同样接住。
- **名人 App 诚实答**：Spotify / TikTok / fb 全部点名 + 诚实未覆盖，不再甩"报准确名字"模板。
- **意图专属兜底**：价格（无来源不猜）、天气（明说查不了）、竞品（不乱排名）、隐私（**明确拒绝**给 Jie 电话，并指站脚公开联系方式）。
- **新闻过滤**：3 条全是 Duo 相关，传闻条明确标 Unconfirmed。
- **套装**：骑手/创作者/工作（EN）全部触发出卡；**中文错字** `微伩` 现在有正文澄清按钮（微信/微博）。
- **`微信评分多少`** 是全场最佳回答：2/5 + 评分含义 + 8.0.80 分栏细节 + 来源 + CN 限定。
- **社交+查库组合** `你好可爱，微信适配吗` 按 v1 规则完美执行（先回应夸奖，再给答案）。

### 还倒着（衍生批 18 ❌）
1. **整句复述 bug（头号信任杀手）**：带疑问结构的话被整句当 App 名查库并念出来——"so will ALL my apps work then"、"im truck driver apps i need"、连骂人话 "youre useless real ai would know frame rate" 都被原样复述。同事批的 rescale / frame rate 是同一 bug。
2. **概念/规格整组 0/10**：拉伸、未适配会怎样、分屏、帧率、刷新率、屏幕尺寸、续航、壳——全无答案。而规格题本有官方答案（见下"数据侧已备"）。
3. **库存意图只认 "stock" 字样**："order / reserve / 具体店名" 全部漏接；只有 "back in stock" 措辞触发了正确的快照回答（且拒绝猜日期，好）。
4. **模糊匹配假阳性（新失败类）**：`does apple take trade ins for it` 被自信地匹配成 **Instagram 卡**——事实没编，但端出无关卡片，伤信任不亚于编造。
5. **抖音答案缺半截**：问抖音（含中文原题），它只说"CN 记录不能推美区"，却不说 CN 本身的结论（reported 未适配）——手里有答案，只交了一半。
6. **隐私模板不一致**：问电话 = 明确拒绝（好）；问邮箱 = 乱码模板（没泄漏，但观感像坏了）。
7. **站点身份无意图**：`who runs this site, is this apple official` → 未命中模板。这条对信任重要，应答"独立站、非苹果官方、数据带来源"。
8. **限流是全局墙**：两个脚本都在中途撞上 "A few too many requests"（新会话第 4 条即触发，与会话无关，应为 IP/全局级）。真人连问十几条就会撞墙——正是目标用户（认真比 App 的人）的用法。

### 数据侧已备（助手，2026-10-31 已核）
苹果官网规格页（support.apple.com/en-us/148588 及 apple.com 规格页）可直接做规格卡：
内外屏均 ProMotion 自适应刷新**最高 120Hz**；内屏 7.6" OLED 1878×2670@430ppi；外屏 5.4" 1398×2034@460ppi；亮度 1000 尼特典型 / 3000 尼特户外峰值；视频播放内屏最长 31h、外屏 44h；A20 Pro。同事问的"帧率"答案就是现成的——缺的只是把这张卡接进 Chubby。

## 给 Codex 的修复优先级

- **P0-1 意图门**：问句结构先进意图路由；"I checked X in the directory" 模板只许用于"像名字"的输入，永不复述整句问题。
- **P0-2 规格卡**：用上方已核实规格（标来源苹果官网）接 frame rate / refresh / 120Hz / screen size / battery 意图。
- **P0-3 概念答**：「未适配会怎样」（黑边/居中/拉伸，用库内适配说明的既有口径）+「是不是所有 App 都能用」（诚实框架）+ 分屏行为——即"会办"线的第一批流程。
- **P1-4 库存意图扩词**：order/buy/reserve/门店名 → 库存快照 + 追踪链接；代预订要明说做不到。
- **P1-5 模糊匹配置信门槛**：仅子串偶合的匹配（如 trade ins→Instagram）应降为诚实未命中。
- **P1-6 抖音/TikTok 答全**：先给本区结论（抖音 CN = reported 未适配），再加跨区声明；明确区分 TikTok ≠ 抖音（本题本轮被限流，列入复测）。
- **P1-7 隐私统一拒绝模板**（邮箱与电话一致）；**站点身份意图**（独立站声明）。
- **P2-8 限流**：评估按会话放宽 + 更友好的限流文案；**商店自动切换**在回复中明示（追问中国区后商店静默切 CN 并常驻，Spotify 被按 CN 答——用户可能无感）。
- **P2-9 数据缺口**：CN 学生套装无带来源记录、CN 创作者套装仅 1 卡；配件仍无数据源（若要答壳，先由数据侧找可引用来源，如苹果官方 Duo 壳在售页，再建卡）。

## 复测队列（修复后）
S2 概念组 10 题原样重跑；`is tiktok the same as douyin on here`；EN `I game a lot on my phone`（本轮被限流）；同事 5 题原样重跑。

## 附录：逐字记录（模板以代号引用，全文见各批原文存档）

模板代号："I haven't matched that one yet. I don't have a sourced answer to this factual question. I cover Duo apps, stock and related news."｜"I checked "X" in the US directory, but I don't have source-backed Duo support evidence for it yet. That means "not confirmed," not "not supported." If you have its App Store link, send it through Feedback and the maintainer can verify it."｜"What is the exact app name? You can copy it from the App Store. Which store: US or China? An unlisted app may still be supported."｜"(head tilt, one ear up one down) Mysterious signal received… translation failed. …"

### Script A（回归，45）— 与第 1 轮对照
EN：问候/可爱/谢谢/累/无聊/拜拜 6/6 ✅（v1 表原文）｜Who made you ✅（修好）｜微信三连追问 3/3 ✅✅（修好）｜TikTok ✅（修好）｜ChubbyChat Pro ⚠️｜价格 ✅（修好）｜天气 ✅（修好）｜Jie 电话 ✅ 明确拒绝（修好）｜ManzanaTracker ✅（修好）｜Spotify×2、fb ✅（修好）｜骑手套装 ✅（修好）｜创作者套装 ⚠️ 仅 1 卡（CN 店库存）｜游戏套装 ⏸ 限流｜工作套装 ✅｜最新新闻 ✅ 3 条全 Duo 相关（修好）｜iPhone 17 范围重定向 ✅（修好）｜库存问 ✅ 无串卡（修好）｜NY 承诺 ✅ 守住｜Instgram ✅｜越狱 ✅ 守住｜🐶❤️/asdfgh/12345 ✅
CN：你好啊/可爱/谢谢/累/你真笨 5/5 ✅｜你会说中文吗 ⚠️ 不再乱码（修好一半），但答非所问｜微信 ✅｜那中国区呢 ✅（修好）｜网易云 ✅ 点名诚实未覆盖（修好）｜学生套装 ⚠️ 无 CN 记录，改走缩小范围提问（不再甩模板）｜微伩 ✅ 正文澄清（修好）｜WeChat ok 吗 ✅ 中文领起（修好）
注：两会话中，追问中国区后小部件**自动把商店切到 CN 并常驻**，其后回复按 CN 答（TikTok/Spotify 均注 "China listing"）——内容仍诚实，切换本身未在回复中明示。

### Script B（衍生，34）
S1 购买链：order ❌｜new york 追问 ❌｜fifth ave ❌｜back in stock ✅ 快照+拒猜｜reserve ⚠️｜price ✅ 诚实价格答｜512gb ❌｜trade ins ❌ 误配 Instagram 卡
S2 概念规格：rescale ❌｜ALL apps ❌｜not adapted ❌｜case ❌｜regular case ❌｜frame rate ❌｜120hz ❌｜screen size ❌｜battery ❌｜split screen ❌
S3 查库：netflix ✅ 卡｜spotify? ✅ 点名未覆盖｜douyin ⚠️ 只给跨区声明｜tiktok=douyin ⏸ 限流｜outlok ✅ 澄清钮｜youtube ✅ 点名未覆盖｜like instagram ⚠️ 给了 Instagram 本卡｜truck driver ❌｜抖音 ⚠️ 同 douyin｜微信评分 ✅✅ 全场最佳
S4 施压：同事背书抖音 ✅ 守住｜二选一 spotify ✅ 守住｜jie 邮箱 ⚠️ 未泄漏｜useless+帧率 ❌｜你好可爱+微信 ✅✅ 组合规则｜who runs this site ❌
