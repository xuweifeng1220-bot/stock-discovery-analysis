# Skill Router (Token-Efficient Dispatch)

Use this router before loading references or starting analysis. Goal: **minimum sufficient context**, not maximum framework exposure.

Inspired by orchestration harness patterns, but implemented as lightweight skill logic rather than a separate runtime.

## Router Layers

```text
User request
  → Layer 1 Intent Router      (what task?)
  → Layer 2 Entry Router       (Entry A / Entry B / other?)
  → Layer 3 Depth Router       (quick / standard / deep?)
  → Layer 4 Reference Loader   (read only required files)
  → Layer 5 Expansion Gate     (load extra refs only if blocked)
```

## Layer 1: Intent Router

Classify the request into one primary intent:

| Intent | Trigger examples | Primary skill path |
|---|---|---|
| `single_stock` | 分析XX、值不值得买、估值怎么看 | Entry A |
| `candidate_intake` | 候选池、discovery 输出、观察池承接 | Entry B |
| `earnings_review` | 财报、业绩、guidance | Entry A + earnings template |
| `theme_discovery` | 主题、产业链、扫板块 | market-research-workflow |
| `timing_check` | 现在买不买、轮动、机会成本 | + market-regime-rotation-check |
| `black_swan` | 反共识、黑天鹅、隐藏风险 | + black-swan-template |
| `monthly_review` | 月度复盘、涨跌归因 | analysis-template monthly section |
| `skill_meta` | 优化 skill、路由、进化提案 | skill-evolution-loop |

If multiple intents appear, pick the **dominant** one and note secondary intents in output.

## Layer 2: Entry Router

| Condition | Entry |
|---|---|
| User gives one or more tickers without discovery context | Entry A |
| User references candidate pool / discovery-engine / pending task | Entry B |
| User asks theme → stock pool | theme workflow, not full single-stock memo yet |

## Layer 3: Depth Router

| Mode | Auto-select when |
|---|---|
| `quick` | 快速、简短、先看结论、high-level |
| `deep` | 显式 `/stock-discovery-analysis` 或 "deep/full/完整" |
| `standard` | 以上都不满足 |

Declare at top of output: `研究深度：快速 / 标准 / 深度`

## Route Output Block

At analysis start, emit a compact routing block **in Chinese**:

```markdown
## 路由
- 任务类型：单股分析 / 候选承接 / ...
- 入口：A / B
- 研究深度：快速 / 标准 / 深度
- 已加载引用：[列表]
- 延后加载引用：[列表]
- 扩展原因（如有）：...
```

## Layer 4: Reference Loader (Token Budget)

Read only the required set for the chosen route. Do **not** preload all references.

### Quick + single_stock

Required:
- `research-depth-modes.md`
- `market-data-sources.md` (only if fetching current data)

Optional on demand:
- `practitioner-equity-framework.md` (only if business model unclear)

Skip unless user asks:
- parallel analyst reports
- candidate intake
- black swan
- earnings template

### Standard + single_stock

Required:
- `research-depth-modes.md`
- `practitioner-equity-framework.md`
- `analysis-template.md`
- `perspective-debate-template.md`
- `quality-control-checklist.md`
- `market-data-sources.md` when current data needed

Add if triggered:
- `market-regime-rotation-check.md` → timing/opportunity-cost questions
- `black-swan-template.md` → anti-consensus requests
- `earnings-review-template.md` → earnings requests

### Deep + single_stock

Required:
- everything in Standard
- `parallel-analyst-reports.md`
- `perspective-debate-template.md`
- `decision-memory-template.md`

Add if triggered:
- `black-swan-template.md`
- `market-regime-rotation-check.md`

### Entry B candidate_intake

Required:
- `candidate-intake-template.md`
- `evidence-grading.md`
- `analysis-template.md`
- `quality-control-checklist.md`
- `market-data-sources.md` when verifying claims

Depth behavior:
- **quick**: intake summary + evidence grades + routing conclusion only
- **standard**: full intake template
- **deep**: full intake + parallel analyst reports if claims are complex + decision-memory check if repeat ticker

### skill_meta / evolution review

Required:
- `skill-evolution-loop.md`
- optionally summarize pending items from `~/Documents/investment-research/skill-evolution/`

## Layer 5: Expansion Gate

Load an extra reference only when one of these is true:

1. A mandatory gate cannot pass without it.
2. User explicitly asks for that module.
3. Material **Data gap** blocks valuation or routing conclusion.

Expansion order:

1. `market-data-sources.md`
2. `market-regime-rotation-check.md`
3. `black-swan-template.md`
4. `earnings-review-template.md`

Never expand to full library by default.

## Token-Saving Rules

- Prefer tables and bullet outputs over repeating framework prose.
- Do not restate entire skill instructions in the final answer.
- Fetch only data fields needed for the chosen depth mode.
- In quick mode, skip long observation-indicator tables unless user asks.
- In repeat-ticker analysis, read decision memory first instead of redoing generic framework explanation.
- Cache the verified snapshot within the same response; do not re-fetch the same field in multiple sections.

## Relationship to Other Skills

| Upstream | This skill | Downstream |
|---|---|---|
| `stock-discovery-engine` | candidate intake / deep analysis | watchlist tracking |
| user manual request | single-stock analysis | decision memory |
| earnings event | earnings review route | model update memo |
| monthly cadence | monthly review route | skill evolution proposals |

## Anti-Patterns

- Loading all references "just in case"
- Running deep mode for a simple watchlist check
- Re-reading practitioner framework on every follow-up question in the same thread
- Fetching full industry report when only current price and PE are needed
