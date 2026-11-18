# which-jev

> 按场景选决策引擎，而不是按聚合分。[English](README.md)

Jev 类决策模型为速度而生，尺寸又约束了通用性——没有哪台引擎能通吃所有位置。聚合指数（Jev Decision Index、Artificial Analysis v2）回答"谁最聪明"；**which-jev** 回答"**这个场景、这个延迟与成本预算下，用哪台**"。

本仓是 [awesome-jev-prompts](https://github.com/vicfei/awesome-jev-prompts) 的伴生仓——那边是"怎么问"，这边是"问谁"。

## 什么是 suite

一个场景 = 一个 suite = held-out 测试集 + runner + 榜单。所有 suite 强制同构四列：

| 准确率 | 校准 | 延迟 | 成本 |
|---|---|---|---|
| 场景指标（accuracy / nDCG@5 / AUROC …） | ECE + Brier——阈值路由在概率上，概率质量就是产品 | 每次决策的 p50 + p95 | 每千次决策的 $ |

方法论继承 [jev-rag-zh-benchmark](https://github.com/vicfei/jev-rag-zh-benchmark)：钉死引擎版本、配对置信区间、冻结问题措辞、每次运行公开报告。

## Suites

| # | 场景 | 状态 |
|---|---|---|
| 0 | [中文 RAG 重排](https://github.com/vicfei/jev-rag-zh-benchmark) | 已运行——在原仓进行，作为创始 suite 吸收 |
| 1 | [工具审批与准入控制](suites/tool-approval/) | 建设中——场景卡已在 [ajp](https://github.com/vicfei/awesome-jev-prompts/blob/main/README.zh-CN.md#which-jev按场景选引擎) 上线；测试集与 runner 随后 |

想加的位置（提 issue 提案）：上下文压缩（keep-or-drop）、路由与分诊、筛查门（注入/信号-噪声）、轻量具身（游戏步决策）、数据工作流判断。

## 地面规则

1. **held-out 纪律**：测试条目永不作为训练用途发布、永不与任何训练数据收录重叠；方法学与聚合结果公开。污染是独立性的死穴——Decision Index 藏起 Full 分测试集就是这个原因。
2. **厂商可提交，须标注**：任何人可提交；厂商运行的行明确标记，每次运行必须可复现——钉死版本、公开问题措辞。
3. **数字保持动态**：榜单实时渲染，README 行文永不写死当前分数。
4. **场景优先**：suite 为回答选型问题而存在——不能改变工程师选择的，不发。

## 状态

v0 骨架（2026-11-16）：登记表、地面规则、suite #0 挂接、suite #1 立项。runner 与首个榜单随后。贡献从 issue 开始：描述你的场景与它该裁决的选型问题。

## 许可

内容 CC0。runner 代码落地后采用 Apache-2.0。
