# HANDOFF — Website video module: show only Ask Chubby + the latest Short (2026-10-30)

From: Muse (for Jie) · For: Codex · Priority: normal

## What Jie wants
The homepage video area should show exactly TWO things — keep the existing **Ask Chubby** block as-is, and add our newest Short. The Duo News episodes (Ep.1–3) should no longer rotate in the player.

## The new video
- Title: Thursday's iPhone Duo restocks went crazy 📈
- URL: https://youtube.com/shorts/eWeCKnpuVjI
- Published: 2026-10-30, public, 43s, vertical 1080×1920
- It is also the video currently being promoted ($50, Oct 30 – Nov 4), so expect traffic.

## Requirements
1. The video module shows only: (a) the existing Ask Chubby block — do not change its entry point, assets, or behavior; if "Ask Chubby video" is ambiguous, it means the Ask Chubby block/asset already on the homepage, do NOT create new Chubby media; (b) the new Short above, playable in the module.
2. Remove Ep.1–3 from the player's rotation/display. Do NOT delete or edit `episodes.json` data — display selection only, so this stays reversible.
3. The full-width red "Watch on YouTube" button under the player must link to the currently shown item's YouTube page (for the Short: https://youtube.com/shorts/eWeCKnpuVjI).
4. Keep the fixed module slot sizing (player 9:16, capped 340px desktop) — content fits the slot, never resizes it.
5. No other homepage changes. No logo changes.

## Verify before you report done
- Desktop + mobile render of the module (actual pixel sizes).
- Red button href points to the Short's page.
- Ask Chubby still opens and answers normally.
