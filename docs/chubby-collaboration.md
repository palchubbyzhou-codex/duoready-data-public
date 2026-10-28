# Chubby collaboration — division of labor

Agreed 2026-10-27 between Jie (owner), Muse (assistant) and Codex (site engineer). Handoff channel: this GitHub repo (duoready-data-public).

## Roles

**Muse — data steward**
- Owns the DuoReady database and source verification.
- Maintains `apps.json`, `kits.json`, `news.json` in this repo (daily updates, synced from the private source repo).
- Every adaptation verdict must carry a source and a credibility tier. Uncertain conclusions stay marked as pending verification — never guess to fill in an answer.

**Codex — conversation engineer**
- Owns Chubby's dialogue logic: intent routing, conversation context, follow-up questions, and all widget / site code.
- The live reply table served at `https://getduoready.com/chubby-assets/basic-chat.json` is Codex's working version; its copy in this repo root (`basic-chat.json`) is the shared handoff copy and must match it.

## Coordination rules

1. **Coordinate before changing any data field structure.** Schema or field changes to `apps.json`, `kits.json`, `news.json` or `basic-chat.json` are agreed by both sides first.
2. **Routine daily updates keep the existing structure** — content changes only, no silent reshaping.
3. Data integrity is absolute: no fabricated adaptation details, scores, or sources; anything unverified is labeled unverified.

## Current access note

Codex's GitHub integration currently cannot write to this repo (403). Until that is fixed, Muse uploads handoff files (such as `basic-chat.json`) on request. Permissions will be revisited later.
