# Homepage module size spec (owner rule, 2026-10-28)

Problem reported by Jie on the live site: when the Duo News player is showing, that module balloons; the slideshow renders smaller. Modules must never resize per content. From now on every media module is a FIXED slot; content fits the slot — never the other way round.

## Fixed slots
| Module | Slot aspect | Asset size | Fit rule |
|---|---|---|---|
| News banner (slideshow) | **Responsive slot** (desktop fixed height ~287px, mobile ~300px) | Masters: desktop **2400×800 (3:1)** + mobile **1080×1080 (1:1 re-layout)**, EN+ZH WebP — Codex banner spec 2026-10-28, see slideshow/README.md | Site handles rounding; images keep square corners, no UI baked in |
| Featured carousel ("A closer look") | **16:9** — the identical box as the slideshow | content designed to 16:9 | cover; rotating items (app feature ↔ slide) must not change the box height by a single pixel |
| Duo News player (Shorts) | **9:16** | YouTube Shorts embed | fixed rail width (≤400px desktop); the player's height comes from 9:16 only — it must not stretch its column or push sibling modules around |
| Stock tracker card / Star Sweep | unchanged grid cells | — | heights set by the grid, not by content |

## Hard rules
1. **Slot first**: a module's rendered width/height is decided by this spec and the grid — never by the natural size of the image/video inside it.
2. **No distortion**: never stretch media to fill (`object-fit: fill` is banned). Use cover (crop) or contain on the module's own background color.
3. **No layout shift between states**: playing a different episode, rotating the carousel, or swapping EN/ZH must not change any module's box size.
4. **Breakpoints**: on mobile, slots go full-width but keep the same aspect ratios (16:9 stays 16:9, 9:16 stays 9:16).
5. New asset types (future modules) get their slot size added to this table BEFORE shipping — pixel size is decided up front, not improvised per piece of content.

Assets already comply: slides are mastered at 1920×1080. The fix is layout-side only.
