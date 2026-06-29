# Candidate Intake Template

Use this workflow only when the user asks to analyze a candidate from a discovery output, candidate pool, task queue, pending list, proposed/approved task, or watchlist intake.

## Candidate Intake Flow

Candidate stock -> fact organization -> evidence grading -> AI hypotheses -> user hypotheses -> conflicts -> unknowns -> executability review -> final routing.

Before deep analysis, collect or request:

- Ticker and company name.
- Candidate source.
- Why it was discovered.
- Value-chain / industry segment.
- Growth versus price mismatch.
- Capital migration thesis in the value chain.
- Known data gaps.
- Discovery-stage review conclusion.

If candidate-source information is missing, proceed only with clearly marked **Data gap** and ask for the smallest missing inputs.

## Output Template

# 候选承接分析：{股票代码} {公司名}

## 1. 结论

| 项目 | 判断 |
|---|---|
| 当前结论 | 建议进入观察池 / 退回候选池 / 建议剔除 / 等待用户确认 |
| 置信度 | 高 / 中 / 低 |
| 核心理由 | 2-4 条 |
| 最大风险 | 1-3 条 |
| 下一步动作 | 明确可执行动作 |

## 2. 候选来源

| 字段 | 内容 |
|---|---|
| 来源 | stock-discovery-engine / 用户指定 / 其他 |
| 产业链 | 例如 AI 内存链 / 电力 / 光互连 |
| 环节 | 例如 HBM 检测量测 / 光器件 / AI 服务器 |
| discovery 理由 | 为什么被挖出来 |
| 增长/股价错配 | 营收/利润增速 vs 3/6/12 个月股价涨幅 |
| discovery 数据缺口 | discovery 阶段缺什么 |

## 3. 事实层

Only include public facts: business, financials, price action, valuation, announcements, orders/contracts, management guidance.

| 事实 | 证据来源 | 证据等级 | 备注 |
|---|---|---|---|

## 4. AI 假设 vs 用户假设

| 类型 | 假设 | 证据等级 | 是否需要确认 |
|---|---|---|---|
| AI 假设 |  | C/D | 是/否 |
| 用户假设 |  | 用户提供 | 是/否 |

## 5. 冲突点

Check conflicts between AI hypotheses and user hypotheses, facts and market expectations, value-chain logic and financials, valuation and fundamentals.

| 冲突 | 说明 | 处理 |
|---|---|---|

## 6. 未知项

Track unavailable or weakly evidenced information: orders, backlog, inventory quality, contract details, customer mix, capacity utilization, real gross margin, price trend, undisclosed segment revenue.

| 未知项 | 重要性 | 当前可得性 | 下一步验证 |
|---|---|---|---|

## 7. 可执行性审核

Executability means whether the candidate deserves watchlist tracking, not whether it should be bought.

| 审核项 | 通过/不通过/待验证 | 理由 |
|---|---|---|
| 增长真实性 |  |  |
| 增长持续性 |  |  |
| 高频验证 |  |  |
| 市场未定价原因 |  |  |
| 催化剂 |  |  |
| 赔率 |  |  |
| 证伪条件 |  |  |
| 用户假设确认 |  |  |

## 8. 估值与情景

Continue using `analysis-template.md` bear/base/bull valuation. If data is insufficient, mark **Data gap** and do not force a conclusion.

## 9. 最终流转建议

| 建议 | 条件 | 人工门禁 |
|---|---|---|
| 进入观察池 / 退回候选池 / 剔除 / 等待用户确认 | 说明条件 | 必须用户确认 |

## Routing Rules

Use only these final conclusions:

- **建议进入观察池**: A/B evidence supports the core judgment; key user assumptions do not conflict; catalysts and invalidation conditions are clear; risk-reward is worth tracking.
- **退回候选池**: facts are interesting but unknowns are too large; thesis mainly relies on C/D evidence; growth persistence cannot be verified; price already reflects the thesis.
- **建议剔除**: growth is unsustainable; financial/valuation mismatch is disproved; value-chain position is weak; risk-reward is poor; core thesis conflicts with facts.
- **等待用户确认**: AI hypotheses may conflict with user hypotheses; user industry information is needed; information is insufficient to advance or reject.
