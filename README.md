# which-jev

> Pick a decision engine by scenario, not by aggregate score. [中文版](README.zh-CN.md)

Jev-class decision models are sized for speed, and size bounds generality — no single engine wins every seat. Aggregate indices (Jev Decision Index, Artificial Analysis v2) answer "which model is smartest"; **which-jev** answers "**which engine fits this scenario, under this latency and cost budget**".

Companion to [awesome-jev-prompts](https://github.com/vicfei/awesome-jev-prompts) — that library is *how to ask*; this is *whom to ask*.

## What a suite is

One scenario = one suite = a held-out test set + a runner + a leaderboard. Every suite reports the same mandatory columns:

| Accuracy | Calibration | Latency | Cost |
|---|---|---|---|
| scenario metric (accuracy / nDCG@5 / AUROC …) | ECE + Brier — thresholds route on probabilities, so quality of probabilities is the product | p50 + p95 per decision | $ per 1k decisions |

Methodology inherited from [jev-rag-zh-benchmark](https://github.com/vicfei/jev-rag-zh-benchmark): pinned engine versions, paired confidence intervals, frozen question wording, public per-run reports.

## Suites

| # | Scenario | Status |
|---|---|---|
| 0 | [Chinese RAG reranking](https://github.com/vicfei/jev-rag-zh-benchmark) | live — runs in its own repo, absorbed here as the founding suite |
| 1 | [Tool approval & admission control](suites/tool-approval/) | building — scenario card already live in [ajp](https://github.com/vicfei/awesome-jev-prompts#which-jev--pick-an-engine-by-scenario); test set + runner next |

Seats we want next (propose via issue): context compaction (keep-or-drop), routing & triage, screening gates (injection / signal-vs-noise), embodied-lite (game-step decisions), data-workflow judgments.

## Ground rules

1. **Held-out discipline.** Test items are never published for training use and never overlap any training-data listing; methodology and aggregates stay public. Contamination is what kills independence — the reason the Decision Index hides its Full-score tests.
2. **Vendor runs welcome, labeled.** Anyone may submit; vendor-run rows are marked, and every run must be reproducible — pinned versions, public question wording.
3. **Numbers stay dynamic.** Leaderboards render live; README prose never hardcodes current scores.
4. **Scenario first.** A suite exists to settle a seat's selection question — if it wouldn't change an engineer's choice, it doesn't ship.

## Status

v0 skeleton (2026-11-18): registry, ground rules, suite #0 linked, suite #1 chartered. Runner + first leaderboard land next. Contributions start with an issue: describe your scenario and the decision it should settle.

## License

CC0 (content). Runner code, when it lands, under Apache-2.0.
