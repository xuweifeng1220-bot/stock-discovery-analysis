# Quality-Control Checklist

Run this checklist before finalizing any stock discovery, single-stock memo, candidate intake, earnings review, buy-worthiness judgment, or black-swan analysis. Missing mandatory items must be fixed before final output. If they cannot be fixed because data is unavailable, the final answer must include **Data gap**.

## Mandatory Acceptance Criteria

For single-stock analysis, the final answer must include:

- Company business essence before final investment strategy, unless the user explicitly asks for a quick verdict.
- First-principles decomposition: real demand, customer payment reason, value-chain position, unit economics, and hard-to-copy constraint.
- Macro market and industry environment: market risk appetite, current mainline themes, stronger competing themes, industry cycle stage, and sector-relative position.
- Current price and market cap with source/date, or a clearly labeled **Data gap**.
- Latest revenue and profit/cash-flow/margin data, or available substitutes.
- Bear/base/bull scenario valuation.
- Assumptions behind each scenario.
- Implied market cap or value range.
- Upside/downside versus current market cap, if current market cap is available.
- Current market expectation: what the price already seems to assume.
- Catalysts, risks, and invalidation conditions.
- Market mainline and opportunity-cost check when judging whether it is worth buying now.
- Key observation indicators for business, financials, industry, capital flow, technical/execution, and catalysts.
- Role-based debate before final strategy: Bull, Conservative, Neutral, and Portfolio Manager synthesis.
- `Data gap` plus `Next research` when material evidence is missing.

If any item is missing and not marked as **Data gap**, the output fails QC.

If the user explicitly invoked `stock-discovery-analysis`, the output also fails QC when it silently compresses the template into a partial or shortcut format without the user's consent.

For Candidate Intake, the final answer must include:

- Candidate source, discovery reason, value-chain segment, growth/price mismatch, discovery data gaps, or clearly labeled **Data gap**.
- Fact layer separated from AI hypotheses and user hypotheses.
- Evidence grades A/B/C/D for key facts and assumptions.
- Conflicts among facts, market expectations, value-chain logic, valuation, AI hypotheses, and user hypotheses.
- Unknown items and next verification steps.
- Executability review: growth reality, growth persistence, high-frequency verification, market mispricing reason, catalysts, risk-reward, invalidation, and user-confirmation need.
- Final conclusion limited to: **建议进入观察池**, **退回候选池**, **建议剔除**, or **等待用户确认**.
- Human gate: analysis may recommend routing, but user must confirm before formal watchlist status changes.

If the core thesis mainly relies on C/D evidence, the output fails QC unless the conclusion is **退回候选池** or **等待用户确认**.

## Thesis Quality

Reject or downgrade the conclusion if:

- The thesis depends mainly on a headline.
- The business model is not explained.
- The real value-chain beneficiary is unclear.
- The analysis cannot explain who pays, why they pay, and who captures margin.
- The idea is "good industry" without proving "good stock."
- The thesis relies on labels such as "leader", "scarcity", "domestic substitution", or "AI/technology option" without reducing them to demand, value creation, value capture, and competitive constraints.

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
- Material valuation gaps are listed but not pursued even though obvious next-step verification exists.

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

## Structure Quality

For single-stock analysis, flag these structure errors:

- The response collapses into a quick or compressed memo even though the user explicitly invoked the skill and did not ask for a short version.
- The final investment action appears before business essence, market environment, valuation, risks, and role-based debate.
- Macro commentary becomes generic and does not answer whether market capital is willing to buy this direction now.
- Role-based debate appears before the core analysis or replaces valuation work.
- Key observation indicators are missing, vague, or not connected to future buy/add/reduce/exit conditions.
- The analysis fails to distinguish new capital from existing position handling when strategy is discussed.
- `Data gap` is present, but `Next research` does not explain what to verify next and why it matters.

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
8. Did I apply first-principles reasoning to the company business essence?
9. Did I place role-based debate before final strategy, not before the analysis?
10. If this is Candidate Intake, did I keep the conclusion within the allowed four routing outcomes?
11. If this is Candidate Intake, did I prevent C/D evidence from promoting a candidate into the watchlist?
12. If material evidence was missing, did I provide both `Data gap` and `Next research` instead of stopping at a generic disclaimer?
13. Did I avoid deterministic investment advice while still providing conditional valuation ranges?

## Anti-Patterns

Bad output:

> Company is a good business but valuation is expensive.

Reason: no current data, no assumptions, no scenarios, no risk-reward, no invalidation.

Good output pattern:

> At current market cap X as of DATE/SOURCE, the base case assumes revenue A, margin B, and valuation multiple C, implying value D. Bear/base/bull ranges show downside/upside of E/F/G. The thesis fails if growth, margin, or market regime assumptions break.
