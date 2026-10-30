# Microsoft Outlook on iPhone Duo — Research Dossier

**Prepared for:** DuoReady feature article (first "精品" per-app feature)
**Research dates:** 2026-10-29 – 2026-10-30 (all sources retrieved in this window)
**Scope note:** DuoReady's database had NO Outlook record before this research. Everything below is built from named external sources. Claims are graded: **[PRIMARY]** = Microsoft/Apple first-party; **[TRACKER]** = third-party build/tracker analysis; **[PRESS]** = reputable press; **[UNVERIFIED]** = single weak/conflicting source, do not publish as fact.

---

## 1. Verdict (with confidence)

**Outlook is PARTIALLY adapted today — the base adaptation is real and official, but the headline two-pane layout is NOT yet live. "听说完全适配了" is only half true.**

**Confidence: HIGH** for the split itself (two first-party sources agree: Microsoft's own release notes + Apple's Newsroom). **MEDIUM** on fine visual details (no owner reports, no hands-on video, and no official screenshot of Outlook on a Duo exists publicly as of 2026-10-29).

What is true right now (as of 2026-10-29):

- ✅ **Microsoft officially added iPhone Duo support in Outlook iOS 5.2641.0 (release notes dated 2026-10-23, the Duo's launch day):** "Added support for iPhone Duo, with layouts optimized for side-by-side multitasking and smoother resizing during orientation and window-size changes." — Microsoft Learn **[PRIMARY]**
- ✅ **The app fills the inner display (no letterbox) and uses Apple's Duo APIs** — built with the iOS 27.1 SDK, uses `systemTraitsAffectingVerticalBarEdge`; status "Fits" for both 5.2641.0 (checked 2026-10-21) and 5.2642.0 (checked 2026-10-27). — FitsDuo tracker **[TRACKER]**
- ❌ **The signature in-app two-pane layout — inbox next to a full message — has NOT shipped yet.** Apple (2026-10-22): "In the coming weeks, Microsoft Word and Outlook will roll out a desktop-class experience… Outlook's inbox next to a full message." FitsDuo repeats: the two-pane inbox "arrives in the coming weeks." No source found confirms it is live in 5.2641.0 or 5.2642.0. **[PRIMARY + TRACKER agree]**
- ❓ **Zero owner reports, zero hands-on videos, zero official screenshots of Outlook on a Duo** were found anywhere (EN + ZH web, YouTube, Bilibili). FitsDuo literally shows "No reports from owners yet."

**Editorial recommendation (for the DuoReady record, not a sourced fact):** classify as *partially adapted / in transition* (过渡档）, not "fully adapted." Suggested editorial score: **3/5** — full-screen fill + official support are real, but the defining two-pane experience is still a promise with a "coming weeks" date. Re-check when a build newer than 5.2642.0 ships or when owner reports appear; the score should rise once the two-pane is confirmed live.

---

## 2. Evidence by source type

### 2.1 Official — Microsoft

| Source | Date | What it says | URL |
|---|---|---|---|
| Microsoft Learn, *Release notes for Outlook Mobile* | Entry dated 2026-10-23 (page retrieved 2026-10-29; newest entry on the page was 5.2641.0) | **Build 5.2641.0, iOS: "Added support for iPhone Duo, with layouts optimized for side-by-side multitasking and smoother resizing during orientation and window-size changes."** This is the single strongest source in this dossier: it proves Microsoft shipped *something* Duo-specific, and its wording is about filling/resizing/Split View behavior — it does NOT claim an in-app two-pane inbox. | https://learn.microsoft.com/en-us/officeupdates/release-notes-outlook-mobile |
| App Store "What's New" for 5.2642.0 (2026-10-26), as transcribed by Eleven Forum (2026-10-27) and visible on the App Store page (which showed 5.2641.0 "2d ago" with the same generic text) | 2026-10-26/27 | Only generic text: "performance improvements and bug fixes." **Neither 5.2641.0 nor 5.2642.0 mentions Duo in its App Store notes** — the Duo line lives only in the Microsoft Learn notes. Useful honesty point for the article: users cannot discover Duo support from the App Store changelog. | App Store page: https://apps.apple.com/us/app/microsoft-outlook/id951937596?platform=mac (URL as returned by search; app id 951937596) |
| Microsoft Support, *Can I read emails in full screen view?* | n/a (standing doc) | On Outlook mobile (iOS/Android) the reading pane has an expand icon (diagonal arrows, top right) to expand a message to full screen — i.e., on phone-class layouts the message view is a pane you expand, not a permanent desktop-style second column. Relevant to the slab-vs-Duo comparison. | https://support.microsoft.com/en-us/outlook/can-i-read-emails-in-full-screen-view?nochrome= |

**Not found:** no Microsoft blog post (Microsoft 365 Blog / Outlook Blog) dedicated to iPhone Duo support was found in searches. Microsoft's only first-party Duo statement located is the Learn release-note line above.

### 2.2 Official — Apple

| Source | Date | What it says | URL |
|---|---|---|---|
| Apple Newsroom, *Developers bring incredible new app experiences to iPhone Duo* | 2026-10-22 | "In the coming weeks, Microsoft Word and Outlook will roll out a desktop-class experience… Outlook's inbox next to a full message." Apple also describes the platform behavior: same aspect ratio on both displays so apps scale proportionally between outer/inner screens; Split View brings two apps side by side to iPhone for the first time; iOS 27.1 SDK apps "expand to multi-column configurations on the inner display." **Note: the article contains NO Outlook image** — its illustrated apps include Zoom, Slack, Fantastical, Netflix, Prime Video, MLB, Lyft. Outlook is text-only. | https://www.apple.com/newsroom/2026/10/developers-bring-incredible-new-app-experiences-to-iphone-duo/ |
| Apple Newsroom (Taiwan, Traditional Chinese edition of the same article) | 2026-10-22 | Same content in Chinese: 「未來幾週，《Microsoft Word》和《Outlook》將陸續推出媲美桌面電腦的隨身體驗…Outlook 的收件匣則與完整郵件並排呈現。」 This is the source most Chinese coverage traces back to. | https://www.apple.com/tw/newsroom/2026/10/developers-bring-incredible-new-app-experiences-to-iphone-duo/ |

### 2.3 Third-party trackers

| Source | What it says | URL |
|---|---|---|
| **FitsDuo — "Does Microsoft Outlook fit iPhone Duo?"** (page crawled 2026-10-30) | Status: **"Fits"** — "Microsoft Outlook fills the inner screen and adapts when you fold." Version 5.2642.0 (Oct 26, 2026), built with iOS 27.1 SDK, "uses Apple's iPhone Duo APIs" (`systemTraitsAffectingVerticalBarEdge`), "Confirmed by Apple" as a source. Version history: 5.2642.0 = Fits (checked Oct 27), 5.2641.0 = Fits (checked Oct 21). **Crucially, the same page says: "Microsoft is still improving it: Apple says the inbox next to a full message arrives in the coming weeks."** And: "What owners report — No reports from owners yet." FAQ: "Is Microsoft Outlook letterboxed on iPhone Duo? No. Microsoft Outlook fills the inner display." Method caveat: FitsDuo's verdict is build/SDK analysis + Apple's statement, not owner hands-on — so "fills the screen" is solid, but no human has publicly documented the actual in-app layout. | https://fitsduo.com/apps/outlook |
| **FoldHunt (Chinese-language tracker)** | **STALE / OUTDATED — do not cite as current.** Its Outlook page (data as of 2026-10-06, pre-launch) says "尚未宣佈… 在更新之前不會鋪滿內螢幕" (not announced; won't fill the inner screen until updated) and its app list says only "Apple 称 Duo 版本将在未来几周内推出." This directly contradicts Microsoft's 5.2641.0 release notes and FitsDuo's checks. Included here as a **documented source conflict**: Chinese-language trackers lag the English ones on this app. | https://foldhunt.com/zh-hant/apps/microsoft-outlook/ and https://foldhunt.com/zh/iphone-duo/apps/ |

### 2.4 US web / press

| Source | Date | What it says | URL |
|---|---|---|---|
| MacRumors, Joe Rossignol, *Apple Reveals More Than 50 Apps That Will Be Updated for iPhone Duo* | 2026-10-22 | Restates Apple: "In the coming weeks… Microsoft's Word and Outlook apps will roll out a 'desktop-class experience' that includes… Outlook's inbox visible next to a full message." | https://www.macrumors.com/2026/10/22/apple-highlights-iphone-duo-apps/ |
| Thurrott, *Apple's App Store Adds New Badge for Apps Optimized for iPhone Duo* | 2026-10-22 | Lists "Netflix, Prime Video, Word, Outlook, Zoom, Slack, Salesforce, Fantastical…" among apps "that have been optimized" — but this is Apple's forward-looking list; the same article notes (via The Verge's review) that iOS 27-optimized apps auto-adjust in landscape on the inner screen, a weaker tier than a native Duo layout. Thurrott (Paul Thurrott) had pre-ordered a Duo, but no Outlook hands-on from him was found (his unit/travel timing put hands-on later). | https://www.thurrott.com/apple/343134/apples-app-store-adds-new-badge-for-apps-optimized-for-iphone-duo |
| Gadget Hacks, *Made for iPhone Duo Badge: What It Means — and What It Doesn't* | ~2026-10-28 | Important context for the whole category: per Apple's Oct 5 developer guidance, the "Made for iPhone Duo" badge is triggered by **submitting Duo screenshots in App Store Connect** — Apple has not publicly described a separate functional certification. The article repeats that Microsoft's layouts were announced Oct 22 as rolling out "in the coming weeks," so availability "shouldn't be assumed until the relevant app updates arrive." | https://apple.gadgethacks.com/news/what-the-made-for-iphone-duo-badge-actually-confirms/ |
| TheStreet, *Apple's $1,999 iPhone Duo appears to have an app problem* | ~2026-10-23 | "Microsoft Word and Outlook won't have their Duo versions at launch, with updates expected 'in the coming weeks'" (attributed to Gadget Review). Also notes MKBHD called app support the Duo's biggest launch weakness. | https://www.thestreet.com/technology/apples-1999-iphone-duo-appears-to-have-an-app-problem |
| The Verge (via secondary summaries) | 2026-10-22/23 | The Verge's Duo coverage frames Word/Outlook side-by-side layouts as *expected/announced*, and its hands-on (Nilay Patel) found some "optimized" apps (e.g., Instagram) still buggy. **No Verge text found that documents the actual Outlook layout on a Duo.** Also note: The Verge's Oct 23 hinge-damage reportage is a *device* story, not an Outlook issue. | (secondary summaries retrieved via search; no direct Verge Outlook claim captured) |
| Windows Central | — | **No Duo-specific Outlook article found.** Searches surfaced Windows Central Duo coverage generally, but nothing documenting Outlook's Duo layout. Recorded as a genuine negative. | — |
| Reddit | — | No Reddit thread documenting Outlook's on-device Duo layout was found in searches. (Reddit appears in Duo coverage for hinge-crack photos — device issue, not Outlook.) Recorded as a genuine negative. | — |
| 9to5Mac | — | 9to5Mac covered the Duo app ecosystem, but no Outlook-specific hands-on/claim beyond Apple's announcement was captured. Recorded as: no independent Outlook layout evidence from 9to5Mac. | — |

### 2.5 YouTube

**Finding: NO hands-on video specifically showing Microsoft Outlook running on an iPhone Duo was found** (searches run 2026-10-29/30, EN). Specifically:

- Full-device reviews checked for Outlook content — MKBHD's iPhone Duo review, Matt Talks Tech's review (video ID GrSEPcfRbnc), ITSub's review — none documents an Outlook layout segment in any indexed description, transcript snippet, or written follow-up. These reviews focus on hardware, the crease, and marquee apps (Instagram/Netflix/Zoom class).
- "Best apps for iPhone Duo" roundups located in text form (e.g., thinkscribe.ai's table, 9io.ai's Oct 26 roundup "The best apps for iPhone Duo so far") list Outlook only with Apple's wording ("inbox next to a full message," status "Shown by Apple" / "coming later") — i.e., they are relaying the announcement, not showing the app.
- **Consequence for the feature article:** there is currently no video evidence of what Outlook actually looks like unfolded on a Duo. Any article claim about the visual layout must rest on the Microsoft/Apple text sources above, and the absence of hands-on footage is itself a reportable fact ("one week after launch, nobody has filmed it — because the two-pane isn't out yet" is consistent with all evidence).

### 2.6 Chinese web （中文网）

**Finding: NO Outlook-specific hands-on content found on Bilibili, Xiaohongshu, Zhihu, SMZDM, or Weibo.** Chinese coverage of Outlook-on-Duo consists entirely of translations/relays of Apple's Oct 22 Newsroom line.

- 何同学 （老师好我叫何同学， Bilibili) published a 25-app iPhone Duo adaptation test reporting roughly 80% of tested apps NOT adapted; the test focused on Chinese domestic apps — Outlook was not a featured subject. (Retrieved via search summaries 2026-10-29; treat the "80%" figure as his video's framing, not an Outlook data point.)
- Sina's Duo app-adaptation coverage names overseas productivity apps Zoom and Slack as early adapters; **Outlook is not named** in the Sina pieces retrieved. Sina/Weibo in Chinese **To
...[truncated 19863 chars]