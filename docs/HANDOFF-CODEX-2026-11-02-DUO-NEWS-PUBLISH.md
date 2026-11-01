# Handoff for Codex — Publish THE DUO NEWS (original editorial) to the site

Prepared by Muse, 2026-11-01. Status: prompt ready; the publish happens on the evening of
2026-11-02, AFTER Jie approves the first Duo News package. Only the items Muse inserts into
news.json with date 2026-11-02 are the approved set — the review gate guarantees nothing
unapproved lands there that day.

Background (Jie's decision, 2026-11-01): THE DUO NEWS becomes DuoReady's OWN editorial
column. No link roundups, no reshared headlines. Every item is written by us, in our words,
with our own images, on our own URLs. Sources remain only as a small-print attribution line
at the bottom of each article. These pages are also future ad inventory — build them clean.

## The prompt (Jie pastes this to Codex)

把公开仓 news.json 里 date = 2026-11-02 的全部新条目发布到网站的 THE DUO NEWS 栏目，要求：

1. 数据源只认公开仓（duoready-data-public）根目录的 news.json 与 assets/duo-news/2026-11-02/
   里的配图，按记录里的图片文件名对应使用，不要自己另找图、不要热链任何外部图片。
2. 首页只保留一个新闻模块，就是 THE DUO NEWS（我们原创的这一套）；现有的聚合式
   "Apple News" 模块与之合并/替换，不要两个新闻区并排。
3. 每条新闻生成我们自己的文章页（沿用站内现有的 URL 规律），最新在前；页面内容 =
   我们的标题 + 我们的正文 + 我们的配图 + 日期；正文末尾一行小字标来源
   （例：来源：MacRumors），来源链接只出现在那行小字里，正文不做外链导流。
4. 中英文跟随站内现有的语言切换机制，双语字段都用上，不要只发英文。
5. 不要动 apps.json / scores-100.json 的任何数据和显示逻辑，不要碰直播和 tracker。
6. 发布后自检并回报：首页 Duo News 模块正常、每条文章页 URL 返回 200、图片在桌面和
   手机宽度都正常显示、没有溢出或重叠。发现数据里缺字段先停下来报告，不要编造补齐。

## After Codex reports done

Muse verifies the live site (homepage module + every new article URL + images, desktop
and mobile widths) before Jie is told it is live.
