# Stock Discovery Analysis

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

面向 **A 股 / 港股 / 美股 / ETF / 主题板块** 的 AI 投研分析 Skill，适用于 Cursor、Codex 等 Agent 环境。

将商业本质、三情景估值、预期差、证据分级、市场主线、方法论辩论、候选池承接整合为一套可复用投研流程。**AI 起草，人类拍板**——不提供自动交易或确定性买卖指令。

---

## 安装

```bash
npx skills add xuweifeng1220-bot/stock-discovery-analysis
```

---

## 快速使用

**标准分析（默认）：**
```text
/stock-discovery-analysis 分析某某公司，看估值预期差和主要风险
```

**深度全流程：**
```text
/stock-discovery-analysis deep 分析 NVDA
```

**快速结论：**
```text
快速看一下寒武纪，先给结论
```

**候选池承接：**
```text
/stock-discovery-analysis 承接这个 discovery 候选，做 Candidate Intake
```

---

## 设计理念

| 原则 | 说明 |
|---|---|
| 商业本质优先 | 先看公司如何赚钱，再看消息 |
| 估值是锚 | 任何观点映射到 bear/base/bull 区间 |
| 预期差驱动 | 收益来自认知差，不是共识复述 |
| 消息是催化剂 | 验证主逻辑，不替代主逻辑 |
| 技术面是风控 | 仓位 / 止损 / 异常应对 |
| 人机分工 | AI 结构化研究，人类最终判断 |
| 中文输出 | 用户可见内容默认简体中文 |

---

## 架构概览

```text
                         ┌─────────────────┐
                         │   用户请求       │
                         └────────┬────────┘
                                  ▼
                    ┌─────────────────────────┐
                    │   skill-router          │
                    │ 意图 → 入口 → 深度 → 引用 │
                    └────────┬────────────────┘
              ┌─────────────────┼─────────────────┐
              ▼                 ▼                 ▼
        Entry A            Entry B          主题/财报/复盘
       独立单股分析        候选池承接         专项路由
              │                 │
              └────────┬────────┘
                       ▼
              Verified Data Snapshot
              （A/H/US 双源验证）
                       ▼
         ┌─────────────┴─────────────┐
         ▼                           ▼
    [深度] 四通道报告            商业本质 + 行业环境
    [深度] A/B/C 可研究性              │
         └─────────────┬─────────────┘
                       ▼
              三情景估值 + 预期差
                       ▼
              方法论辩论（四视角）
                       ▼
              最终策略 + QC 质检
                       ▼
         [可选] Skill 进化提案（人工审核）
```

---

## 研究深度三模式

| 模式 | 何时触发 | 输出特点 | Token |
|---|---|---|---|
| **快速** | 「快速 / 简短 / 先看结论」 | 结论卡 + 3 理由 + 3 风险 | 低 |
| **标准** | 默认 | 完整 memo + 方法论辩论 | 中 |
| **深度** | `/stock-discovery-analysis` 或「深度 / 完整」 | 四通道 + A/B/C 评级 + 视角评分表 + 决策记忆 | 高 |

---

## 两条分析入口

### Entry A — 独立单股分析

直接给股票代码或名称，不依赖 discovery 上下文。

### Entry B — 候选池承接

来自 `stock-discovery-engine`、候选池、任务队列的候选标的。

结论四选一：**建议进入观察池 / 退回候选池 / 建议剔除 / 等待用户确认**

---

## Reference 模块

| 模块 | 文件 | 作用 |
|---|---|---|
| 路由 | `skill-router.md` | 意图识别、深度选择、最小引用加载 |
| 深度模式 | `research-depth-modes.md` | 快速 / 标准 / 深度定义 |
| 核心方法论 | `practitioner-equity-framework.md` | 商业原型、估值纪律、消息边界 |
| 单股模板 | `analysis-template.md` | 研报结构与输出格式 |
| 方法论辩论 | `perspective-debate-template.md` | 四视角对抗 + Facilitator |
| 四通道报告 | `parallel-analyst-reports.md` | 基本面 / 新闻 / 情绪 / 技术 |
| 数据源 | `market-data-sources.md` | A/H/US 双源交叉验证 |
| 市场主线 | `market-regime-rotation-check.md` | 现在值不值得买 |
| 候选承接 | `candidate-intake-template.md` | 候选池 intake 模板 |
| 证据分级 | `evidence-grading.md` | A/B/C/D 规则 |
| 决策记忆 | `decision-memory-template.md` | 同标的重复分析 continuity |
| Skill 进化 | `skill-evolution-loop.md` | 学习提案 + 人工审核 |
| 质检 | `quality-control-checklist.md` | 输出前 QC |
| 财报 | `earnings-review-template.md` | 业绩点评 |
| 黑天鹅 | `black-swan-template.md` | 反共识推演 |
| 主题挖掘 | `market-research-workflow.md` | 主题 → 股票池 |

---

## 与 stock-discovery-engine 协作

```text
stock-discovery-engine     stock-discovery-analysis
      │                            │
      │  候选池 / 任务队列            │
      └──────────► Entry B ────────►│ 证据分级 + 路由结论
                                    │
                                    ▼
                              Entry A 深度研究
                                    │
                                    ▼
                              观察池 / 决策记忆
```

---

## 决策边界

**可以做：**
- 条件估值区间（悲观 / 中性 / 乐观）
- 研究分类：值得关注 / 观察池 / 回避 / 证据不足
- 失效条件、观察指标、下一步研究

**不可以：**
- 确定性 Buy/Sell 指令
- 自动写入观察池 / 持仓
- 自动修改 skill 文件（进化提案需人工 approve）

---

## 目录结构

```text
.
├── LICENSE
├── README.md                          ← 本文件
└── stock-discovery-analysis/
    ├── SKILL.md                       ← Skill 主入口
    ├── README.md                      ← Skill 内说明
    ├── agents/
    │   └── openai.yaml
    └── references/                    ← 17 个 reference 模板
        ├── skill-router.md
        ├── research-depth-modes.md
        ├── practitioner-equity-framework.md
        ├── analysis-template.md
        ├── perspective-debate-template.md
        ├── parallel-analyst-reports.md
        ├── market-data-sources.md
        ├── market-regime-rotation-check.md
        ├── candidate-intake-template.md
        ├── evidence-grading.md
        ├── decision-memory-template.md
        ├── skill-evolution-loop.md
        ├── quality-control-checklist.md
        ├── earnings-review-template.md
        ├── black-swan-template.md
        ├── market-research-workflow.md
        └── data-source-map.md
```

---

## License

MIT — see [LICENSE](LICENSE).
