# Stock Discovery Analysis

面向 A 股 / 港股 / 美股的 AI 投研分析 Skill。用于个股研究、候选池承接、估值判断、财报点评、市场主线与机会成本评估、月度复盘等场景。

**定位**：投研助手，不是自动交易系统。AI 负责结构化研究与估值测算；最终判断由人完成。

## 安装

```bash
npx skills add xuweifeng1220-bot/stock-discovery-analysis
```

安装后，在 Cursor / Codex 中通过 `/stock-discovery-analysis` 或 `$stock-discovery-analysis` 调用。

## 快速开始

```text
/stock-discovery-analysis 分析 NVDA，重点看估值预期差和 now/not-now
```

```text
/stock-discovery-analysis 承接这个 discovery 候选，做 Candidate Intake
```

```text
快速看一下寒武纪，先给结论
```

## 核心能力

- **商业本质优先**：先看公司如何持续赚钱，再看市场噪音
- **三情景估值**：悲观 / 中性 / 乐观，禁止单靠 PE 判断贵贱
- **预期差驱动**：收益来自认知差，不是 AI 预测随机游走
- **A/H/US 双源验证**：关键财务数据尽量双源交叉验证
- **方法论辩论**：四视角对抗（好生意 / 财务质量 / 逆向 / 长期风险）
- **深度模式四通道**：基本面 / 新闻宏观 / 情绪 / 技术执行
- **候选池承接**：证据分级 A/B/C/D，观察池路由
- **Skill 进化提案**：可学习、可提案，但**不自动改 skill**，需人工审核

## 研究深度（三模式）

| 模式 | 默认触发 | 适用场景 |
|---|---|---|
| **快速** | 说「快速 / 简短 / 先看结论」 | 盘中扫一眼、快速对齐观点 |
| **标准** | 不明确指定时（**默认**） | 日常个股研究、常规决策前 |
| **深度** | 显式 `/stock-discovery-analysis` 或说「深度 / 完整」 | 重要标的、可归档复盘 |

三种模式的决策权限相同：都可给条件估值区间和研究分类（值得关注 / 观察池 / 回避 / 证据不足），都**不能**给确定性买卖指令。

## 两条入口

| 入口 | 场景 |
|---|---|
| **Entry A** | 直接分析某只股票 |
| **Entry B** | 承接 discovery 引擎 / 候选池 / 任务队列输出 |

Entry B 结论只能是：**建议进入观察池 / 退回候选池 / 建议剔除 / 等待用户确认**

## 执行流程

```text
用户请求
  → skill-router（意图 / 入口 / 深度 / 最小引用集）
  → Verified Data Snapshot（双源验证）
  → [深度] AI 可研究性评级 A/B/C
  → [深度] 四通道并行报告
  → 商业本质 → 行业环境 → 三情景估值
  → 方法论辩论 → Facilitator 归纳
  → 最终策略（人类拍板）
  → QC 质检 + [可选] Skill 进化信号
```

## 输出语言

**默认简体中文。** 仅保留必要英文：代码、公司名、PE/EPS/FCF/ROE/EV/DCF 等财务缩写。

## Reference 文件索引

| 文件 | 用途 |
|---|---|
| `skill-router.md` | 路由与 token 优化（先读） |
| `research-depth-modes.md` | 快速 / 标准 / 深度 |
| `practitioner-equity-framework.md` | 核心方法论 |
| `analysis-template.md` | 单股研报模板 |
| `perspective-debate-template.md` | 方法论型辩论 |
| `parallel-analyst-reports.md` | 四通道并行报告（深度） |
| `market-data-sources.md` | A/H/US 双源数据规范 |
| `market-regime-rotation-check.md` | 现在值不值得买 |
| `candidate-intake-template.md` | 候选池承接 |
| `evidence-grading.md` | 证据 A/B/C/D |
| `decision-memory-template.md` | 同标的决策记忆 |
| `skill-evolution-loop.md` | 人工审核的 skill 进化 |
| `quality-control-checklist.md` | 输出前质检 |
| `earnings-review-template.md` | 财报点评 |
| `black-swan-template.md` | 反共识 / 黑天鹅 |
| `market-research-workflow.md` | 主题 → 股票池 |
| `data-source-map.md` | 数据源层级 |

## 与 stock-discovery-engine 的关系

```text
stock-discovery-engine（挖候选）
        ↓
stock-discovery-analysis Entry B（承接审核）
        ↓
观察池跟踪 / 深度研究 Entry A
```

## 决策边界

- 可以提供：条件估值区间、研究分类、失效条件、观察指标
- 不可以：确定性买卖指令、自动改观察池状态、自动交易
- Skill 进化：只提案，不自动修改 skill 文件

## 仓库结构

```text
stock-discovery-analysis/
├── SKILL.md                 # 主入口
├── agents/openai.yaml       # Agent 接口配置
└── references/              # 模板与方法论
```

## License

See [LICENSE](../LICENSE) in repository root.
