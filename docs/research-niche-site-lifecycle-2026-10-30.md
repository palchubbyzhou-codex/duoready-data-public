# 围绕单次产品发布 / 平台时刻的利基工具站：生命周期、生存关键与终局

> 研究框架（不研究参考业务本身）：一个小型独立站，围绕一个新产品/新形态发布做三件事——(a) 维护“哪些 App 已适配/兼容”的目录，(b) 24/7 实时库存追踪，(c) 发布相关新闻/视频。本报告用同类站点的真实案例回答：这类站通常活多久、怎么死、怎么活、最后值多少钱。
>
> 证据等级标注：**【实地核查】**=2026-10-30 本研究在浏览器中打开原站确认；**【一手/权威】**=当事人、平台、市场平台官方数据；**【二手报道】**=媒体转述；**【估算/推演】**=本报告基于案例的归纳或示意计算，不是实测数据。凡未标注来源的时长判断均为归纳估算。

## 摘要

1. **这类站的“需求”不是被竞争打死的，而是被事件本身的结束杀死的。** 库存追踪的需求寿命 = 缺货时长（PS5 约 26 个月，2020-11 至 2023-01 Sony 官方宣布缺货结束）；兼容目录的需求寿命 = 过渡期时长（Apple Silicon 约 31 个月，2020-11 首批 M1 Mac 至 2023-06 过渡完成）；平台目录的需求寿命可以短到 6 周（Apple 在 Vision Pro 发售 6 周后亲自上线网页版 visionOS App Store）。
2. **最常见的四种终局，按本研究案例频率排序：僵尸化（站点还在、内容停更）＞ 彻底关停/域名失效 ＞ 转型为更宽的媒体/通讯品牌 ＞ 出售。** 本研究没有找到任何一个“单产品库存追踪站/兼容目录站”在 Flippa/Empire Flippers 公开出售并披露价格的案例——出售更多发生在已经转型为泛品类内容站之后。
3. **活过 2–3 年的站点没有一个靠“把第一波做得更好”活下来，全部靠换赛道或降成本**：NowInStock 把追踪引擎轮换到下一个缺货品类（Switch 2、RTX 5090）；RoaringApps 把同一个兼容数据库复用到 13 个 OS 版本、存活 15 年以上且只有一人运营；Matt Swider 把 100 万追踪者迁移成 Substack 消费科技通讯 The Shortcut。
4. **钱的量级要泼冷水**：内容站当前市场成交倍数约为年利润的 2.3–2.9 倍（约合月利润 28–35 倍，行情差或流量下滑时跌至约 1.1 倍年利润）；一个平台期月访问量 5 万量级的小站，展示广告示意收入约每月数百至一千多美元。峰值期的收入不可外推——买家按最近 12 个月利润定价，衰减中的站点倍数和利润会同时缩水。

---

## (1) 生命周期曲线与各阶段时长

### 1.1 典型曲线（基于下列案例的归纳【估算/推演】）

```
流量
 ▲
 │        ╭── 峰值（发布+稀缺期）
 │       ╱ ╲
 │      ╱   ╲___ 衰减（供给正常化/目录补完/官方工具上线）
 │     ╱        ╲________ 长尾平台期（常青搜索词残值）
 │    ╱ 预热期                 ╲___（或跌至近零→关停）
 │___╱________________________________________▶ 时间
    公布    发售        约18–36个月处出现“终局抉择点”
```

### 1.2 各阶段时长：用真实事件锚定

| 阶段 | 库存追踪型 | 兼容目录型 | 平台/App 目录型 |
|---|---|---|---|
| 预热期（公布→发售） | PS5：2020-09 开预购→11-12 发售，约 2 个月 | M1：2020-06-22 Apple 宣布“两年过渡计划”→2020-11 首批 M1 Mac，约 5 个月【一手/权威，MacRumors】 | Vision Pro：2023-06 公布→2024-02-02 发售，约 8 个月 |
| 峰值期（需求>>供给 或 信息差最大） | PS5：2020-11→2022 年中，约 20 个月；Sony 称供应在 2022 年末改善、2022-12 为历史销量最大月【一手/权威】 | M1：2020-11→约 2022 年，主流应用陆续原生化，查询从“能不能用”变成个别长尾应用 | Vision Pro：2024-02 发售当月；600+ 原生应用上线【二手报道，AppleInsider】 |
| 衰减触发点（可精确到日） | **2023-01-05**：Sony SIE CEO Jim Ryan 在 CES 宣布“PS5 缺货结束”、累计售出 3,000 万台【一手/权威，PlayStation Lifestyle 报道 CES 发言】 | **2023-06-05**：M2 Ultra Mac Pro 发布，Apple 宣布 Apple Silicon 过渡完成、不再销售任何 Intel Mac【一手/权威，MacRumors】 | **2024-03-15**：Apple 上线网页版 visionOS App Store（发售后仅 6 周），非头显用户可直接浏览全部应用【一手/权威，MacRumors】 |
| 从发售到触发点的总时长 | **约 26 个月** | **约 31 个月**（且 Apple 自己预告了“约两年”，实际近三年） | **约 6 周**（目录的信息差部分）；硬件需求衰减约 10–22 个月（见 4.4） |
| 长尾平台期 | 追踪页变成价格/促销页；NowInStock 的 PS5 历史页到 2026-10 仍在逐条更新库存记录【实地核查/索引】，但已不是首页主推 | “Does X work on M1/M5”类查询残存多年；Does It ARM 到 2026 年仍在更新（见 4.2） | 取决于装机量：Vision Pro 2024 年出货约 39 万台（IDC 估算）决定了天花板极低 |

另一个更短的极端样本——**Vaccine Hunters Canada**（疫苗预约“库存”追踪，志愿者运营）：2021-03-19 上线，峰值期约 3–5 个月，2021-08-31 即停止社交渠道日常更新、转自助工具，2022-03-19 上线整一年时正式关闭。创始人明确表示关闭主因是“疫苗已广泛可得，人们不再需要费力搜索”【二手报道，CTV 转述】。**即：当稀缺期只有几个月时，这类站的完整生命周期可以短至 5–12 个月。**

### 1.3 与宏观模型的对照

- Gartner 官方对炒作周期的说明是：一项创新走完整个周期“通常需要三到五年”，且有些会在途中掉队【一手/权威，Gartner】。本研究的工具站案例普遍比这更快衰减（6 周–31 个月），原因是工具站吃的是**信息差/稀缺差**，不是技术采用曲线本身。
- 学术参照：数字人文在线项目遗弃研究（ADHO DH2018）估算在线项目的平均寿命约 **5 年**【一手/权威，会议论文】——注意这是有机构资助的项目，对一人利基站只能作上限参照。

---

## (2) 主要死因

按在本研究案例中出现的频率与致命程度排序：

### 死因 1：底层事件结束——供给正常化 / 过渡完成 / 目录“补完”（最主要）
- PS5：2023-01 Sony 官方宣布缺货结束，此后“restock”从刚需词变成促销词【一手/权威】。
- Apple Silicon：2023-06 过渡完成；此后新 Mac 全部为 Apple Silicon，“是否兼容”对新买家不再是问题。终局还在继续收紧：macOS Tahoe（26）是最后一个支持 Intel 的版本，macOS 27 是最后一个提供通用 Rosetta 2 的版本【二手报道，Macworld 等】——目录的历史使命在制度上被写死。
- 目录补完的实证：Is Apple Silicon Ready 首页条目在 2024-02-25 集中更新一批之后，只剩下 2024-09、2025-01 的零星条目——不是站长先放弃，而是**可追踪的新变化先枯竭**【实地核查】。

### 死因 2：平台方亲自下场（platform envelopment）
- Vision Pro 发售时第三方目录的核心卖点是“没有头显就看不了 visionOS App Store”【一手/权威，9to5Mac 2024-01-30 对目录站的报道原文即以此为卖点】；2024-03-15 Apple 自己上线网页版 App Store，该卖点 6 周内归零【一手/权威，MacRumors】。
- 同型先例：iPhone X 时期 Apple 自己也上线了到店库存查询工具，iStockNow 的差异只剩“全球地图鸟瞰”【二手报道，MacRumors 2017】。
- Vision Pro 生态内的 Spatial Station（空间视频分享应用）2026 年关停时给出的理由正是：Apple 原生 Spatial Gallery 上线、YouTube 原生应用上线、用户活跃下降，“不再可持续”，且该应用免费无广告、存储与基础设施成本由开发者自担【二手报道，PiunikaWeb 转述其关停声明】——平台下场 + 无变现 + 成本自担，三杀合一。

### 死因 3：数据源 / API 被切断或收费
- 2023 年 2–3 月 Twitter 取消免费 API：新价格为 Basic 100 美元/月、企业版约 42,000 美元/月【一手/权威，TechCrunch 2023-03-29】；Tweetbot、Twitterrific 等第三方客户端同年 1 月被关停，大量机器人/小工具宣布停止运营【二手报道，Engadget】。依赖单一平台 API 做提醒、抓取、分发的追踪站，这一刀是即时死亡。
- 库存追踪同理：其数据源是零售商页面/接口，零售商改版、加验证码或封爬虫即失效——本研究未找到 NowInStock 等站就此的公开自述，故此条对追踪站为**机制推断【估算/推演】**，API 部分为已证实的通用风险。

### 死因 4：Google 算法依赖
- HouseFresh（独立产品评测小站）：2024 年 3 月核心更新后 Google 流量 **-91%**，日访客从 4,000 跌到 200【一手/权威，Search Engine Land 2024-05-02 引其自述】。
- Retro Dodo（独立复古游戏站）：自 2023 年 9 月 Helpful Content Update 以来自然流量与收入 **-85%**，自称现金耗尽【二手报道】。
- 市场层面：Flippa 官方称算法变化后内容站成交量下降 **37%**【一手/权威，Flippa 估值指南】——算法不只杀流量，还直接杀退出价格。

### 死因 5：变现太弱，撑不到第二波
- 兼容目录的典型变现只剩捐赠：Is Apple Silicon Ready 页脚的主要变现入口是 “Buy me a coffee”【实地核查】；RoaringApps 运营者 Bryce Cameron 在 Buy Me a Coffee 页面明说会员费是用来覆盖“服务器和邮件通知服务”等月度成本，且是“一人运营”【一手/权威】。
- 硬件联盟营销的结构性问题：追踪器把用户送去买一台 400–500 美元的硬件，看似客单价高，但用户**一生只买一次**、买完即流失，且缺货期根本无货可卖、无佣金可拿——流量最大时恰恰是最不赚钱时（此条为机制分析【估算/推演】，与 Stock Informer/NowInStock 均在页面显著披露联盟链接的事实一致【实地核查】）。

### 死因 6：创始人倦怠 / 人力不可持续
- Vaccine Hunters Canada：100 名志愿者、每天数百条更新，运转约 6 个月后先转自动化自助工具、再关闭【二手报道】——人力密集型实时更新是第一个断的环节。
- RoaringApps 反证了同一规律：能活 15 年的形态是“众包数据库 + 一人低强度维护”，而不是编辑部式日更【一手/权威】。

### 死因 7：底层产品本身失败（装机量天花板）
- Vision Pro：IDC 估算 2024 年出货约 **390,000 台**；组装厂 Luxshare 于 2025 年初停产一代产品；2025 年第四季度出货估算仅约 45,000 台；Sensor Tower 数据显示 Apple 在美英等市场的数字广告支出削减 **95% 以上**【二手报道，Financial Times 2026-01 报道经多家转述】。围绕它的目录/资讯站面对的不是份额问题，而是池塘本身只有几十万用户。

---

## (3) 活下去的关键

每条都对应至少一个存活案例，不是通用 SEO 建议：

1. **把“工具”做成可轮换的引擎，而不是一次性页面。** NowInStock.net 版权页显示其运营主体存续自 **2005 年**；2026-10 实地核查时，其首页主推已轮换为 Nintendo Switch 2、RTX 5090/5080、RX 9070 XT、宝可梦卡牌等当期缺货品，PS5 只是列表中的普通一项【实地核查】。生存的关键动作发生在 PS5 热潮之内：同一套监控+提醒基础设施（注册、邮件/短信/Telegram/浏览器提醒）平移到下一个稀缺品。
2. **在第一波死前扩品类边界。** Stock Informer（英国）从 PS5/Xbox 擴展到空气炸锅、Dyson Airwrap、iPad 等一切“难买品”，用户评论时间跨度从 2021 年 PS5 一直延续到其他品类【二手报道，Trustpilot 评论】；其 PS5 Pro 页面至今仍在，变现为联盟链接披露【索引】。
3. **把受众变成自有资产（邮件/通讯/社区），再换内容品类。** Matt Swider 在 TechRadar 任职期间以 PS5/Xbox 补货追踪把 Twitter 粉丝从 2020 年初的约 8,000 涨到 2021 年末的 **100 万+**；2021-11-08 离职当天在 Substack 创办 The Shortcut，内容扩为消费科技推荐、评测与优惠【一手/权威，Talking Biz News；涨粉数据为二手人物报道】。The Shortcut 自称通过补货提醒帮助 **400,000 人**买到 PS5，并把同一打法复用到 PS5 Pro、Switch 2 等后续稀缺品【一手/权威，站方自述】。这是本研究里“单品追踪 → 媒体品牌”最完整的成功样本。
4. **众包/自动化把维护成本压到接近零。** RoaringApps 自 2010 年以 wiki 形态起步做 Snow Leopard/Lion 兼容众包【二手报道，Cult of Mac 2011、PowerPage】，此后每个 macOS 版本（含 Apple Silicon、Windows on ARM）只是在同一数据库上加一个维度；运营者自述已覆盖 **13 个 OS 版本**、一人运营、靠会员覆盖服务器成本【一手/权威，Buy Me a Coffee 页面】。Does It ARM 同理：靠用户报告+应用包数据维护，索引显示其条目在抓取前 14 小时仍有更新、收录 3,689 个应用、设备列表已跟进到 M5 机型，变现为 Carbon 开发者广告【索引】——低成本 + 开发者垂直广告，是目录站少见的“健康僵尸以上”状态。
5. **选有复购/常青尾巴的查询，而不是事件词。** “X 应用是否支持 Apple Silicon”在过渡完成后仍有存量 Intel 用户、Rosetta 退场（macOS 27 后）等二次问题；RoaringApps 的老 OS 兼容数据至今仍被搜索。反之，“PS5 restock”在供给正常化后只剩促销价值。
6. **多渠道分发对冲 Google。** 存活案例的提醒通道普遍是邮件+Discord+Telegram+推送多管齐下（Stock Informer、NowInStock 均如此【实地核查/二手报道】）；HouseFresh 在 -91% 后公开表态要“在每个有意义的平台上死磕”【一手/权威，Search Engine Land】，侧面印证单一搜索依赖的脆弱。

---

## (4) 同类站点的最终归宿：具体案例

### 4.1 主机补货/库存追踪站（PS5 / Xbox Series X，2020–2023）

| 站点/账号 | 起点 | 归宿 | 关键证据 |
|---|---|---|---|
| **NowInStock.net**（美国，Troposphere LLC） | 站点存续自 2005 年，PS5 时期为头部追踪站之一 | **存活（引擎轮换型）**：2026-10 仍在线，主推 Switch 2/RTX 50 系等新稀缺品；但其 Site News 栏目停留在 2023 年秋，呈“引擎活、编辑僵”状态 | 【实地核查】首页与版权页 ©2005–2026；PS5 库存历史页 2026-10 仍逐条更新【索引】 |
| **Stock Informer**（英国） | PS5/Xbox 时期以邮件/Discord/Telegram 提醒著称 | **存活（品类泛化型）**：现追踪一切难买消费品，PS5 Pro 页仍在，联盟变现 | 【索引】官网 PS5 Pro 追踪页；Trustpilot 跨品类评论 |
| **Matt Swider / @mattswider → The Shortcut** | 2020 年约 8K 粉丝，靠补货追踪涨至 1M+ | **转型成功（媒体/通讯型）**：2021-11 创办 Substack 消费科技通讯，扩品类并复用追踪打法于后续产品 | 【一手/权威】Talking Biz News；The Shortcut 自述帮助 400K 人买到 PS5 |
| **@PS5stockalerts 等单品 Twitter 账号** | 2021 年时已有 100 万+ 粉丝【二手报道，iTechPost 2021-12】 | **多数沉寂/沦为促销账号**（本研究未能逐一核查每个账号的停更日期，见第 6 节）；其需求基础在 2023-01 供给正常化后消失 | 需求消失点【一手/权威】Sony CES 2023 声明 |
| **Wario64**（对照组） | 游戏优惠聚合账号，早于 PS5 存在 | **存活**：因本来就是“全品类优惠”定位，PS5 只是其内容之一——说明先有宽定位者不受单品周期影响 | 【二手报道】多家媒体将其列为综合优惠/补货信息源 |

### 4.2 Apple Silicon 兼容目录（M1 过渡期，2020–）

| 站点 | 起点 | 归宿 | 关键证据 |
|---|---|---|---|
| **Is Apple Silicon Ready**（isapplesiliconready.com，Abdullah Diaa） | 2020 年 M1 发布期上线，Product Hunt 记录其收录 450+ 应用、530 个 Homebrew 包、15 种语言、支持订阅某应用的适配通知 | **僵尸化**：2026-10-30 实地核查仍在线，但首页最新条目停在 **2025-01-17**（Deezer），再往前是 2024-09 与 2024-02 的批次；站名与标题仍写着 “M1/M2 Processors”；变现仅见 “Buy me a coffee” | 【实地核查】；Product Hunt 页面【索引】 |
| **Does It ARM?**（doesitarm.com） | 2020-11-10 于 Product Hunt 发布 | **存活（低维护型）**：索引抓取显示收录 3,689 个应用、57.5% 已原生，最近条目在抓取前 14 小时更新，设备支持列表已含 M5 机型，挂 Carbon 广告 | 【索引】doesitarm.com 首页与 Product Hunt |
| **RoaringApps**（roaringapps.com，Bryce Cameron） | 2010 年 wiki 起步，2011 年因 OS X Lion 兼容表走红 | **存活（跨周期复用型，本类最长寿）**：同一众包数据库历经 13 个 OS 版本，后扩展到 Apple Silicon 与 Windows on ARM；一人运营，会员/捐赠覆盖服务器与邮件成本；索引显示其应用页近月仍有抓取更新（如条目提及 2025-09 的 macOS 26 版本信息） | 【一手/权威】Buy Me a Coffee 运营者自述；【二手报道】Cult of Mac 2011、Scripting OS X 2017 |

**这一类的分水岭很清晰**：同样做兼容目录，靠人工编辑追新应用的站（Is Apple Silicon Ready）在“可追踪变化枯竭”后停更；靠众包/结构化数据、且把维度扩展到每个新 OS/新芯片的站（RoaringApps、Does It ARM）活了下来。

### 4.3 Apple Store / iPhone 库存查询站

| 站点 | 起点 | 归宿 | 关键证据 |
|---|---|---|---|
| **iStockNow**（istocknow.com） | iPhone 7 时期（2016）已提供全球 Apple Store 实时库存地图（绿/红图钉、按型号/颜色/容量筛选、邮件提醒），iPhone X（2017）、iPhone 11（2019）时期被 MacRumors 多次报道推荐 | **关停**：2021-09 iPhone 13 发布时，MacRumors 论坛用户发帖称“该站似乎已倒闭（that site now seems to be defunct）”求替代品；2026-10-30 本研究实地访问 istocknow.com **连接超时无法打开**，与“已关停”判断一致（见第 6 节保留意见） | 【二手报道】MacRumors 论坛 2021；【实地核查】2026-10-30 超时 |
| 同类替代需求的承接 | — | iPhone 供应在 2017 年后逐代改善，且 Apple 自家到店取货库存查询一直存在，第三方库存地图的信息差逐年变薄；iStockNow 之后再无同量级独立站出现（本研究检索未发现，属负面证据） | 【二手报道】MacRumors 2017 报道 Apple 官方工具与 iStockNow 并存 |

### 4.4 Apple Vision Pro 目录与资讯生态（2024–）

| 站点/产品 | 起点 | 归宿 | 关键证据 |
|---|---|---|---|
| **Apps for Apple Vision Pro**（appsforapplevisionpro.com，MoneyCoach 团队开发） | 2024-01-30/31 被 9to5Mac、TweakTown 报道：发售前唯一能在网页端浏览/提交 visionOS 应用的目录，卖点正是“没有头显就进不了 visionOS App Store” | **关停（域名失效）**：2026-10-30 实地访问该域名 **DNS 无法解析**；其存在价值于 2024-03-15 被 Apple 官方网页版 App Store 直接覆盖 | 【实地核查】DNS 失败；【一手/权威】9to5Mac 2024-01-30、MacRumors 2024-03-15 |
| **appsforapplevision.com**（另一个同名近似目录） | Vision Pro 应用目录 | **存活但体量小**：索引抓取显示收录 438 个应用、标注价格在 7 天内校验——证明该品类没有全灭，而是收缩为极小长尾 | 【索引】其目录页 |
| **Spatial Station**（Vision Pro 空间视频应用/社区） | Vision Pro 生态内受欢迎的空间视频分享应用 | **关停（2026 年）**：官方理由为 Apple Spatial Gallery 与 YouTube 原生应用上线、用户活跃下降、无广告免费模式无法覆盖存储与基础设施成本 | 【二手报道】PiunikaWeb 引关停声明 |
| 底层硬件 | 2024-02-02 发售，$3,499，首发 600+ 原生应用 | IDC 估算 2024 年出货约 39 万台；一代产品 2025 年初停产；2025Q4 估算约 4.5 万台；官方广告支出 -95%+；2025-10 以 M5 版小幅 refresh 续命 | 【二手报道】FT 2026-01 经 iClarified 等转述 IDC/Sensor Tower 数据 |

### 4.5 其他可比终局样本

- **使命终结型关停——Vaccine Hunters Canada**：2021-03-19 上线→约 26.5 万 Twitter 粉丝、100 名志愿者、多市政府合作→2021-08-31 停日常更新转自助工具→2022-03-19 整一年时正式关闭，创始人直言主因是供给充裕后“不再需要费力搜索”【二手报道】。这是“库存/预约追踪站”最干净、最诚实的死法样本：**总寿命 12 个月，活跃寿命约 5 个半月。**
- **算法绞杀型重伤——HouseFresh / Retro Dodo**：未关停，但 -91%/-85% 的流量损失证明：即便底层需求没消失，单一 Google 依赖也能让小站实质性死亡【一手/权威 / 二手报道】。
- **出售型**：本研究在 Flippa/Empire Flippers 公开记录与新闻中**没有找到**上述任何一类单品追踪/兼容目录站的具名成交案例（价格、倍数均无）。能查到的只有市场整体倍数数据（见第 5 节）。合理解释【估算/推演】：这类资产的需求曲线人尽皆知地向下，买家只会在其已转型为泛品类、收入稳定 12 个月以上之后才按内容站定价——届时它已不再是“单品站”。

---

## (5) 钱与估值：变现方式、出售倍数等真实数据

### 5.1 变现方式随生命周期的迁移（案例归纳）

| 阶段 | 主导变现 | 案例依据 |
|---|---|---|
| 峰值期 | 展示广告（流量大但转化差）+ 联盟链接（缺货时无货可卖） | NowInStock/Stock Informer 页面均披露联盟佣金【实地核查/索引】 |
| 衰减期 | 提醒订阅/会员（少数）、捐赠（多数小站的终局） | RoaringApps、Is Apple Silicon Ready 的 Buy Me a Coffee【一手/权威 / 实地核查】 |
| 转型后 | 通讯订阅 + 联盟 + 赞助（The Shortcut 模式）；开发者垂直广告（Does It ARM 的 Carbon 广告） | 【一手/权威 / 索引】 |
| 始终缺席的 | 向被收录方收费上架、卖数据——本研究案例中均无公开证据 | 负面证据 |

### 5.2 展示广告能赚多少：示意测算【估算/推演，费率为二手区间】

二手行业资料给出的每千次会话收入（RPM）区间大致为：AdSense 约 $2–15、高级广告联盟（Mediavine/Raptive）约 $15–35+，且高级联盟有流量门槛（如 Mediavine 低门槛产品约 1,000 会话起、Raptive 约 25,000 月页面浏览起，门槛近年多次变动，见第 6 节）。按此粗算：

- 平台期 **5 万月页面浏览**：约 **$100–1,500/月**（区间取决于广告网络与流量地域构成）；
- 平台期 **1 万月页面浏览**（多数僵尸目录的现实量级）：约 **$20–300/月**——刚好覆盖或略高于服务器+邮件服务的成本线，这正是 RoaringApps 式“会员覆盖成本”模式成为终局的原因；
- 峰值期即便有 **100 万月页面浏览**，按 $10–30 RPM 也只是 **$10,000–30,000/月**，且只持续到供给正常化——**绝不能按峰值月收入年化来估值或做长期预算**。

### 5.3 出售倍数：市场平台一手数据

注意口径：行业长期用“月净利润倍数”报价；**Empire Flippers 已于 2026-09-08 起改用年倍数**【一手/权威，其官方公告】，比较时务必换算（年倍数 ×12 = 月倍数）。

| 数据 | 数值 | 来源与等级 |
|---|---|---|
| Empire Flippers 2026 行业报告的平均挂牌倍数：困境型 | **13.7 倍月利润（=1.1 倍年利润）** | 【一手/权威】Empire Flippers 官方公告引其 2026 State of the Industry Report |
| 同上：典型型 | **27.8 倍月利润（=2.3 倍年利润）** | 同上 |
| 同上：优质型 / 七位数优质型 | **31.1 倍（=2.6 倍年）/ 41 倍（=3.4 倍年）** | 同上 |
| Empire Flippers 历史锚点 | 起家时以约 **20 倍月利润**收购 AdSense 小站著称（自称 “20x Guys”）；累计成交 $600M+、2,683+ 单 | 【一手/权威】同一公告 |
| Flippa 内容站利润倍数 | **2.85 倍年利润**（其估值指南）；且内容站成交量在算法变化后 **-37%** | 【一手/权威】Flippa 官方博客 |
| Flippa H1 2026 实际成交 | 内容站平均 **2.32 倍**、头部四分位 **4.68 倍**（利润倍数） | 【一手/权威】Flippa H1 2026 数据博客（二手转述见 SEO 资讯站，口径为年利润倍数） |

**换算成小站的真实支票【估算/推演】**：平台期月净利润 $500 → 按典型 27.8 倍月倍数约售 **$13,900**；月净利润 $1,000 → 约 **$27,800**；且 Empire Flippers 历史上要求约 $500/月以上利润才接单，更小者只能去 Flippa 且倍数更低。若收入处于下滑趋势，买家会同时压低“利润基数”和“倍数”，困境型 13.7 倍意味着 $1,000/月利润只值约 **$13,700**——不及峰值期几个月的广告收入。这解释了为什么本研究找不到单品站的成功退出案例：**理性的出售窗口在衰减开始之前，而那时创始人通常还相信增长会继续。**

### 5.4 流量残值的基础概率

- Ahrefs 对约 10 亿页面的经典研究：**90.63% 的页面从 Google 获得零自然流量**【二手报道引 Ahrefs 研究】——目录站的大量长尾页面天然落在这一分布里，能持续带量的只有少数头部查询页（版本差异见第 6 节）。

---

## (6) 证据不足或相互矛盾之处

1. **iStockNow 的“关停”没有官方公告**：证据是 2021 年论坛用户一句 “seems to be defunct” + 本研究 2026-10-30 实地访问超时。单次超时理论上可源于临时故障或地域封锁，故结论定为“高度可能已关停”，而非确证。其最后正常运营的公开记录是 iPhone 11 时期（2019）。
2. **单品 Twitter 追踪账号的个体结局未逐一核实**：@PS5stockalerts 等账号 2021 年的粉丝量有报道，但其停更日期、是否转型卖货/删号，本研究未找到可靠二手报道，未逐一登录 X 核查（X 内容对未登录访问限制较多）。报告中只断言其“需求基础于 2023-01 消失”，不断言每个账号的现状。
3. **Vision Pro 出货量全部是估算且口径打架**：Apple 从未公布销量。IDC 经 FT 给出的数字是 2024 年约 39 万台、2025Q4 约 4.5 万台；更早的 2024 年中报道曾有“全年不超过 50 万台”的 IDC 预测与“原计划 300 万台”等互相冲突的说法。本报告采用时间最近、来源链最完整的 IDC/FT 版本，并明确标注为估算。
4. **Ahrefs 的“零流量页面”比例有两个版本**：早期约 10 亿页面研究为 90.63%，后续更大数据集（约 140 亿页面）的二手转述为 96.55%。两者样本与年份不同，不应混用；本报告正文只用 90.63% 并在此说明。
5. **出售倍数的“月倍数 vs 年倍数”混乱是系统性的**：大量二手 SEO 文章仍在引用 30–40 倍“月倍数”的旧行情，也有文章误把 Flippa 的年倍数写成月倍数（如某统计站称“平均 3.03 倍月利润”，实为年口径）。本报告只采用 Empire Flippers 与 Flippa 官方页面的数字，并按其官方换算关系呈现。
6. **广告 RPM 与联盟门槛数字时效性差**：Mediavine/Raptive 的准入门槛与典型 RPM 在 2024–2026 年间多次调整，二手来源互相矛盾（50,000 会话、25,000 页面浏览、$5,000 年广告收入等说法并存）。第 5.2 节的测算应只作数量级参考。
7. **The Shortcut 的订阅/访问数据主要来自站方与宣传性人物报道**：155,000+ 订阅、月访问 150 万等数字出自一份宣传色彩浓厚的 2026 年人物稿，未获 Substack 官方榜单等独立来源交叉验证；本报告正文只采用可交叉验证的部分（2021-11 创办、创办时已有 100 万 Twitter 粉丝、站方自述帮助 400K 人）。
8. **“平均利基站寿命”没有直接统计**：不存在针对“利基内容站”的存活率权威数据集。本报告用三个替代指标拼凑——在线项目平均寿命约 5 年（学术样本，非商业站）、Gartner 周期 3–5 年、以及 Flippa 二手转述称其 H1 2026 成交的内容站平均站龄超过 10 年（幸存者偏差明显：能卖掉的都是活得久的）。三者不可直接等同于“平均利基站能活 X 年”。
9. **NowInStock 的编辑停更判断基于首页新闻列表**：其 Site News 列表实地核查时最新为 2023 年 10 月条目，但不排除新闻改在其他频道发布；“引擎活、编辑僵”的判断中，引擎活跃有库存历史页 2026-10 仍更新的索引证据支持，编辑部分为首页观察。

---

## 来源（主要）

- NowInStock.net 首页与 PS5 库存历史页（实地核查/索引，2026-10-30）：https://www.nowinstock.net/ ；https://www.nowinstock.net/videogaming/consoles/sonyps5/full_history/
- Sony 宣布 PS5 缺货结束（2023-01-05）：https://www.playstationlifestyle.net/2023/01/05/ps5-stock-shortage-over-30m-sold ；https://www.theshortcut.com/p/ps5-stock-shortage-over
- Matt Swider 离职创办 The Shortcut（2021-11）：https://talkingbiznews.com/they-talk-biz-news/techradar-editor-in-chief-swider-leaving-for-substack-newsletter/ ；人物与数据（二手/宣传性）：https://yespress.io/matt-swider
- Is Apple Silicon Ready（实地核查，2026-10-30）：https://isapplesiliconready.com ；Product Hunt：https://www.ProductHunt.com/products/is-apple-silicon-ready/launches/is-apple-silicon-ready?comment=1225060
- Does It ARM（索引，2026-10）：https://doesitarm.com
- RoaringApps 运营者自述（Buy Me a Coffee）：https://buymeacoffee.com/roaringapps?l=de ；2011 年报道：https://www.cultofmac.com/news/roaringapps-crowd-sourced-app-compatibility-database-for-os-x-lion ；起源（wiki，2010）：https://www.powerpage.org/?p=63578
- Apple Silicon 过渡完成（2023-06-05）：https://www.macrumors.com/2023/06/05/m2-ultra-mac-pro-apple-silicon-complete/
- iStockNow 已倒闭讨论（MacRumors 论坛，2021-09）：https://forums.macrumors.com/threads/istocknow-alternative-to-find-13-availability.2311962/ ；iPhone X 时期报道：https://forums.macrumors.com/threads/istocknow-iphone-x.2085584/
- Vision Pro 目录站报道（2024-01-30）：https://9to5mac.com/2024/01/30/find-apple-vision-pro-apps/?extended-comments=1 ；Apple 上线网页版 visionOS App Store（2024-03-15）：https://www.macrumors.com/2024/03/15/visionos-app-store-web/ ；另一存活目录（索引）：https://appsforapplevision.com/apps-directory
- Vision Pro 出货/停产/广告削减（FT 引 IDC/Sensor Tower，2026-01 转述）：https://www.iclarified.com/99513/apple-cuts-vision-pro-production-and-marketing-as-sales-disappoint-report
- Spatial Station 关停（2026）：https://piunikaweb.com/2026/04/15/spatial-station-shut-down-vision-pro-app/
- Vaccine Hunters Canada 关闭（2022-03）：https://en.wikipedia.org/wiki/Vaccine_Hunters_Canada ；2021-08 转自助工具：https://news.kisspr.com/amp/2021/08/31/vaccine-hunters-canada-halt-social-media-posts-pivot-to-self-serve-tools-news-1130_30684.html
- HouseFresh 流量 -91%（Search Engine Land，2024-05-02）：https://searchengineland.com/review-site-google-traffic-affiliate-seo-content-440143
- Twitter API 收费（TechCrunch，2023-03-29）：https://techcrunch.com/2023/03/29/twitter-announces-new-api-with-only-free-basic-and-enterprise-levels/?tpcc=tcplustwitter ；免费 API 关停影响（Engadget）：https://www.engadget.com/twitter-shut-off-its-free-api-and-its-breaking-a-lot-of-apps-222011637.html?src=rss
- Empire Flippers 倍数口径与 2026 报告数据（官方）：https://empireflippers.com/switching-to-annual-multiples/
- Flippa 估值倍数与内容站成交量（官方）：https://flippa.com/blog/business-valuation-multipliers-by-industry/ ；H1 2026 数据：https://flippa.com/blog/ecommerce-valuation-multiples-h1-2026-data/
- 在线项目平均寿命约 5 年（ADHO DH2018）：https://dh2018.adho.org/part-deux-exploring-the-signs-of-abandonment-of-online-digital-humanities-projects/
- Gartner 炒作周期 3–5 年（官方）：https://www.gartner.com/en/documents/6746334
- Stock Informer（索引）：https://www.stockinformer.co.uk/checker-playstation-5-pro-console
