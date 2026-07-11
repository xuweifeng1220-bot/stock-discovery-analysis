# Parallel Analyst Reports

Use this workflow for **standard** and **deep** single-stock research. Generate four independent analyst reports before synthesis. Do not merge them into one narrative until the synthesis step.

Inspired by multi-agent research workflows, but adapted for human-led judgment: these reports are research support, not trading decisions.

## When to Use

- Required in **deep** mode.
- Optional in **standard** mode when multi-channel synthesis improves clarity.
- Optional in **quick** mode only if it materially improves the verdict.

## Generation Order

1. Complete **Verified Data Snapshot** first. See `SKILL.md` gate rules.
2. Produce four parallel reports from the same snapshot.
3. Synthesize into business essence, valuation, and debate sections in `analysis-template.md`.
4. Do not let any single channel override valuation work.

## Report 1: Fundamental Analyst

Focus: business quality, financial durability, competitive position.

Output:

```markdown
### Fundamental Report
- Business model summary:
- Revenue/profit/cash-flow quality:
- Moat or hard constraint:
- Financial red flags:
- Long-term investment potential: strong / mixed / weak
- Key metrics used:
- Confidence: high / medium / low
```

Rules:
- Ground claims in financial statements, filings, or verified substitutes.
- Do not use sentiment or chart patterns as fundamental evidence.
- Flag **Data gap** when key financials are missing.

## Report 2: News / Macro Analyst

Focus: macro context, policy, orders, earnings events, industry shifts.

Output:

```markdown
### News / Macro Report
- Macro backdrop:
- Company-specific events:
- Industry/policy shifts:
| Item | Classification | Materiality | Already Priced In? |
|---|---|---|---|
|  | Core evidence / Catalyst / Noise | high / medium / low | yes / partial / no / unknown |
- Net impact on thesis: supportive / neutral / damaging / unclear
- Confidence: high / medium / low
```

Rules:
- Classify every item as **Core evidence**, **Catalyst**, or **Noise**.
- News verifies thesis; it does not create thesis by itself.
- Prefer primary sources: filings, earnings, orders, guidance, regulation text.

## Report 3: Sentiment Analyst

Focus: short-term market mood, crowding, narrative heat, positioning.

Output:

```markdown
### Sentiment Report
- Short-term sentiment: bullish / mixed / bearish / overheated
- Narrative heat: low / medium / high
- Crowding signal: low / medium / high
- Capital-flow behavior, if visible:
- What sentiment may be pricing ahead of fundamentals:
- Reliability warning: sentiment is auxiliary, not thesis
- Confidence: high / medium / low
```

Rules:
- Treat social media and headline mood as **auxiliary** only.
- For A-shares, down-weight noisy retail sentiment unless confirmed by price/volume and fundamentals.
- Never promote a stock mainly because sentiment is positive.
- Sentiment can explain timing risk, not intrinsic value.

## Report 4: Technical / Execution Analyst

Focus: trend, key levels, volume anomalies, execution risk.

Output:

```markdown
### Technical / Execution Report
- Trend state: uptrend / range / downtrend
- Key support / resistance:
- Volume or pattern anomaly:
- Crowding or exhaustion signal:
- Execution use only:
  - Position sizing implication:
  - Risk level / review trigger:
- What technicals cannot prove:
- Confidence: high / medium / low
```

Rules:
- Technical analysis supports sizing, timing, stop/review triggers, and black-swan defense.
- It does not validate or invalidate the fundamental thesis by itself.
- If exact levels are unavailable, mark **Data gap** and keep conclusions conditional.

## Cross-Report Synthesis Rules

After all four reports:

1. **Agreement**: where do multiple channels point the same way?
2. **Conflict**: where do channels disagree?
3. **Dominant driver**: business/valuation, macro/news, sentiment, or execution?
4. **What remains unknown**:
5. **What would resolve the conflict**:

Use this synthesis to inform:
- Section 1 business essence
- Section 3 valuation and risks
- Section 5 role-based debate

Do not skip to final strategy if the four reports materially conflict without naming the conflict.

## Minimum Quality Bar

A parallel analyst block fails QC if:

- Any report is empty or generic.
- News items lack Core/Catalyst/Noise classification.
- Sentiment is treated as fundamental proof.
- Technical report claims valuation correctness.
- Reports use different price/market-cap snapshots without explanation.
