# Decision Memory Template

Use this template to preserve research continuity across repeated analyses of the same ticker. This is a lightweight adaptation of decision-memory workflows: learn from prior calls, but keep final judgment human.

## Purpose

- Prevent repeating the same thesis mistake on the same stock.
- Track whether prior assumptions held or broke.
- Inject prior lessons into the next analysis without automating trades.

## When to Use

- Re-analyzing a ticker analyzed before.
- Monthly or quarterly review of watchlist names.
- Post-mortem after a large move, earnings event, or thesis invalidation.

## Storage

Preferred local path (user-maintained):

`~/Documents/investment-research/decision-memory/{TICKER}.md`

If no local file exists, ask whether the user has prior notes. Do not invent prior decisions.

## Record Template

```markdown
# Decision Memory: {TICKER} {Company Name}

## Latest Record
- Date:
- Analyst mode: quick / standard / deep
- Final classification: attractive / watchlist / avoid / insufficient evidence
- One-line thesis:
- Key assumptions:
  1.
  2.
  3.
- Bear/base/bull range at the time:
- Invalidation conditions:
- Why now / why not now:
- Human decision: observe / add / hold / reduce / no action
- Confidence: high / medium / low

## What to Watch Next
| Indicator | Trigger | Review Date |
|---|---|---|
|  |  |  |

## Reflection Log
| Date | Event / Move | What Happened | Assumption Status | Lesson | Action |
|---|---|---|---|---|---|
|  |  |  | held / weakened / broken |  |  |

## Open Questions
-
```

## How to Use in the Next Analysis

Before analyzing the same ticker again:

1. Read the latest decision-memory file if available.
2. State what changed since the last record: price, fundamentals, narrative, catalysts, invalidation status.
3. Explicitly answer:
   - Which prior assumptions still hold?
   - Which assumptions broke?
   - Did the market move for the reason we expected?
4. Update or append a new record after the current analysis.

## Reflection Rules

Good reflection:
- Ties outcome back to assumptions, not hindsight storytelling.
- Separates research correctness from execution correctness.
- Notes whether the miss came from facts, valuation, timing, sentiment, or discipline.

Bad reflection:
- "Stock went up, thesis was right" without checking why.
- Rewriting history to match the outcome.
- Treating one event as proof of a permanent framework change.

## Hard Rules

- Decision memory informs research; it does not auto-approve trades.
- Do not overwrite prior records silently; append reflection entries.
- If prior memory conflicts with new facts, surface the conflict explicitly.
- Missing memory is **Data gap**, not permission to ignore history.
