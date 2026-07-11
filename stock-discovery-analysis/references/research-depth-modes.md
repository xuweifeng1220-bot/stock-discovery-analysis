# Research Depth Modes

Choose one depth mode before starting. Depth controls template breadth, not investment authority.

## Mode Selection

| Mode | Trigger | Goal |
|---|---|---|
| **quick** | User asks for quick/short/high-level view | Fast decision support |
| **standard** | Default when skill is not explicitly invoked, or user gives no depth preference | Balanced memo |
| **deep** | User explicitly invokes `stock-discovery-analysis` | Full institutional-style research |

If depth is unclear, default to **standard**.

## Quick Mode

Use when the user wants speed over completeness.

### Required
- Verified Data Snapshot, or explicit **Data gap**
- One-line thesis and confidence
- Final classification: attractive / watchlist / avoid / insufficient evidence
- Top 3 supporting reasons
- Top 3 risks or invalidation triggers
- Bear/base/bull range if enough data exists; otherwise mark **Data gap**
- Human sign-off boundary

### Skip or Compress
- Parallel analyst reports
- Full first-principles decomposition
- Two-round debate
- Long observation-indicator tables

### Not Allowed
- Deterministic buy/sell commands
- Strong valuation claims without snapshot data
- Skipping **Data gap** when price or financials are missing

## Standard Mode

Default balanced research.

### Required
- Full `analysis-template.md` single-stock memo
- Verified Data Snapshot gate
- Business essence, macro/industry, valuation scenarios
- Perspective debate with facilitator verdict via `perspective-debate-template.md`
- Data gap + Next research when needed
- `quality-control-checklist.md`

### Optional
- Parallel analyst reports when they improve clarity
- AI Researchability rating when useful

## Deep Mode

Use for explicit `stock-discovery-analysis` invocation.

### Required
Everything in **standard**, plus:
- `parallel-analyst-reports.md` four-channel reports
- AI Researchability rating (A/B/C)
- Perspective debate with score table and explicit conflicts
- Decision-memory check for repeat tickers via `decision-memory-template.md`
- Full QC with no silent compression

### Extra Expectations
- Backfill material data gaps before finalizing when feasible
- Separate facts, consensus, user assumptions, and AI inference throughout
- Name conflicts between analyst channels explicitly

## Depth vs Authority

Depth mode changes thoroughness, not permissions.

| Output | Allowed in all modes |
|---|---|
| Conditional valuation ranges | Yes |
| Watchlist / avoid / insufficient evidence | Yes |
| Invalidation triggers | Yes |
| Deterministic trade instruction | No |
| Automated watchlist promotion | No |

## Mode Declaration

State the chosen mode near the top of the output:

`研究深度：快速 / 标准 / 深度`

If the user asked for quick but missing data blocks a credible verdict, downgrade confidence and mark **insufficient evidence** rather than fabricating completeness.
