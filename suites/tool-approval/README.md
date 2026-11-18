# Suite 1 — Tool approval & admission control

**The seat:** the gate that runs before every tool call in a coding/agent harness. Decisions: read-only vs destructive; deletes/overwrites user data; leaks credentials; widens permissions.

**Why nothing existing answers it:** HarnessJevBench (vendor-run) covers permission boundaries inside its harness-duty mix; aggregate indices don't slice this seat. Selection here trades **latency (tens of ms) × per-call cost × calibration at the routing threshold** — none of which aggregate scores expose.

**Status:** scenario card live in awesome-jev-prompts ([EN](https://github.com/vicfei/awesome-jev-prompts#which-jev--pick-an-engine-by-scenario) / [中文](https://github.com/vicfei/awesome-jev-prompts/blob/main/README.zh-CN.md#which-jev按场景选引擎)). Test set (held-out) and runner: building — until they land, the per-engine evidence register with sources lives in the ajp card.

**Method note:** thresholds tuned toward false-block (failure asymmetry: a blocked legit call costs a retry; a passed destructive call costs the workspace). Reports will include threshold-sensitivity curves, not single operating points.
