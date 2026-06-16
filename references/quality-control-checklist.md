# Quality-Control Checklist

Run this checklist before finalizing any stock discovery, single-stock memo, earnings review, buy-worthiness judgment, or black-swan analysis. Missing mandatory items must be fixed before final output. If they cannot be fixed because data is unavailable, the final answer must include **Data gap**.

## Mandatory Acceptance Criteria

For single-stock analysis, the final answer must include:

- Current price and market cap with source/date, or a clearly labeled **Data gap**.
- Latest revenue and profit/cash-flow/margin data, or available substitutes.
- Bear/base/bull scenario valuation.
- Assumptions behind each scenario.
- Implied market cap or value range.
- Upside/downside versus current market cap, if current market cap is available.
- Current market expectation: what the price already seems to assume.
- Catalysts, risks, and invalidation conditions.
- Market mainline and opportunity-cost check when judging whether it is worth buying now.

If any item is missing and not marked as **Data gap**, the output fails QC.

## Thesis Quality

Reject or downgrade the conclusion if:

- The thesis depends mainly on a headline.
- The business model is not explained.
- The real value-chain beneficiary is unclear.
- The analysis cannot explain who pays, why they pay, and who captures margin.
- The idea is "good industry" without proving "good stock."

## Valuation Quality

Flag these errors:

- PE is used alone.
- Valuation is replaced by qualitative language despite available data.
- DCF is used without segment-level assumptions for complex businesses.
- TAM is treated as revenue.
- Revenue growth is assumed without margin and capital intensity.
- Optimistic case is mislabeled as base case.
- Valuation already prices the bull case.
- Downside valuation is missing.
- Bear/base/bull scenarios are missing.

## Evidence Quality

Classify every important input:

- Verified fact
- Management claim
- Sell-side estimate
- Market consensus
- User-provided assumption
- AI inference
- Unknown / needs verification

Do not blend these categories.

## Catalyst Quality

Flag weak catalysts:

- News that confirms what the market already knows.
- Policy without order/customer validation.
- One-off event without durable economics.
- Short squeeze or sentiment heat presented as fundamental change.
- Industry growth where listed company exposure is small.

## Risk Quality

Every analysis must include:

- Business risk
- Valuation risk
- Liquidity/crowding risk
- Execution/timing risk
- Invalidation conditions
- Main anti-thesis

## Human Sign-Off

End with a clear boundary:

- What AI can support with data and reasoning
- What remains human judgment
- What evidence should be collected before action

## Final Gate

Before final output, answer:

1. Is the conclusion supported by evidence, or just narrative?
2. What would prove the conclusion wrong?
3. What is already priced in?
4. Is the upside/downside asymmetric?
5. Is this worth deeper research now, or only watchlist?
6. Did I include required current data or explicitly mark Data gap?
7. Did I include bear/base/bull valuation scenarios for single-stock work?
8. Did I avoid deterministic investment advice while still providing conditional valuation ranges?

## Anti-Patterns

Bad output:

> Company is a good business but valuation is expensive.

Reason: no current data, no assumptions, no scenarios, no risk-reward, no invalidation.

Good output pattern:

> At current market cap X as of DATE/SOURCE, the base case assumes revenue A, margin B, and valuation multiple C, implying value D. Bear/base/bull ranges show downside/upside of E/F/G. The thesis fails if growth, margin, or market regime assumptions break.
