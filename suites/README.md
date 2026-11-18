# Suite registry

One scenario = one suite = held-out test set + runner + leaderboard. Mandatory columns: accuracy, ECE/Brier, p50/p95 latency, $ per 1k decisions.

| # | Scenario | Status | Where |
|---|---|---|---|
| 0 | Chinese RAG reranking | live | [jev-rag-zh-benchmark](https://github.com/vicfei/jev-rag-zh-benchmark) (external, founding suite) |
| 1 | Tool approval & admission control | building | [tool-approval/](tool-approval/) |

Adding a suite: open an issue with (a) the scenario's decision rubric, (b) the selection question it settles, (c) why existing benchmarks don't answer it.
