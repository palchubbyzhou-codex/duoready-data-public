# Capability Score Card — 100-point scores for all database apps

Data file: `data/scores-100.json` (private repo) / `scores-100.json` (public mirror root, runtime-readable at
https://raw.githubusercontent.com/palchubbyzhou-codex/duoready-data-public/main/scores-100.json)

## Method (read before designing around these numbers)
- Every app in apps.json already carries a 1–5 `editorial_score`, assigned from its sourced adaptation evidence (see data/SCHEMA.md).
- The 100-point score is a **pure linear rescale**: score_100 = editorial_score × 20. No per-app hand adjustments, no invented precision.
- Resulting bands: 100 Excellent · 80 Great · 60 Good · 40 Limited · 20 Poor.
- Current distribution (130 apps, 2026-10-28): 100 ×32, 80 ×41, 60 ×55, 40 ×2.
- Credibility tier (verified/reported) stays a separate field — it describes our evidence, not the app's capability, and is NOT baked into the score.

## If the score card needs finer granularity
Four discrete values (100/80/60/40) is honest but coarse. For finer scores (e.g. 87), first define sub-dimensions and weights
(e.g. layout use / split-screen & multitasking / fold-state handling / completeness), then scores will be recomputed
from the same sourced adaptation evidence under that rubric — never hand-tweaked per app. That rubric decision is Jie + Codex's.
