---
name: stock-discovery-analysis
description: Stock discovery and equity analysis workflow for screening A/H/US stocks, ETFs, themes, sectors, and individual companies. Use when Codex needs to mine stock ideas, analyze business fundamentals, valuation, industry cycles, catalysts, technical risk controls, monthly review tables, or practitioner-informed investment reasoning based on business essence, market expectations, risk-reward, and human-led final judgment.
---

# Stock Discovery Analysis

## Operating Premise

Use this skill as an **investment research assistant**, not as an autonomous trading system. Provide structured research, assumptions, probability ranges, risk-reward analysis, and invalidation conditions. Do not present deterministic buy/sell instructions.

The agent is allowed and expected to provide **conditional valuation ranges**. It must not provide deterministic buy/sell commands, automated trading decisions, or single-point price targets without assumptions.

Default to the practitioner-informed framework in `references/practitioner-equity-framework.md` when the user asks for stock mining, stock analysis, sector opportunities, valuation gaps, black-swan thinking, monthly review, or experienced investor-style reasoning.

## Mandatory Execution Gates

Before the final answer, complete all applicable gates. Treat these gates as mandatory acceptance criteria, not optional guidance.

1. **Identify task type**: theme research, stock pool discovery, single-stock analysis, earnings review, sector comparison, valuation check, timing/buy-worthiness, technical risk control, or monthly review.
2. **Load required references**:
   - Single-stock analysis: MUST apply `references/analysis-template.md` and `references/quality-control-checklist.md`.
   - Buy-worthiness or timing: MUST also apply `references/market-regime-rotation-check.md`.
   - Earnings review: MUST also apply `references/earnings-review-template.md`.
   - Black-swan / anti-consensus work: MUST also apply `references/black-swan-template.md`.
   - Theme-to-stock discovery: MUST also apply `references/market-research-workflow.md`.
3. **Collect current data when applicable**: current price, market cap, latest financials, valuation snapshot, and source/date.
4. **Separate facts from judgment**: label current data, user assumptions, market consensus, and AI inference.
5. **Produce required valuation output for single-stock work**: bear/base/bull scenarios, assumptions, implied market cap/value range, upside/downside versus current market cap, and key invalidation triggers.
6. **Check market regime when judging "worth buying now"**: current mainline, stronger competing themes, sector rotation stage, and capital opportunity cost.
7. **Run final QC**: apply the quality-control checklist before responding.

If any gate cannot be completed, do not hide the gap. The final answer MUST include a **Data gap** section explaining what is missing and how that limits confidence.

## Core Workflow

1. **Define the question**
   - Classify the task: theme research, stock pool discovery, single-stock analysis, earnings review, sector comparison, valuation check, catalyst review, technical risk control, or monthly review.
   - State the user's market scope: US, Hong Kong, A-share, ETF, commodity-linked assets, or unknown.
   - If current market data, prices, financials, news, or regulatory facts matter, verify them with reliable current sources before analysis.

2. **Route to the right workflow**
   - For theme-to-stock discovery, read `references/market-research-workflow.md`.
   - For buy-worthiness, timing, opportunity cost, sector rotation, or market-mainline questions, read `references/market-regime-rotation-check.md`.
   - For earnings reports, transcripts, guidance, or post-results updates, read `references/earnings-review-template.md`.
   - For data collection or source planning, read `references/data-source-map.md`.
   - For final review before presenting conclusions, read `references/quality-control-checklist.md`.

3. **Separate facts from judgment**
   - Facts: company business, industry structure, financials, valuation, supply-demand, policy, orders, capital flows, price action.
   - Judgment: market expectations, hidden assumptions, probability weights, scenario valuation, timing, risk-reward.
   - Mark data gaps explicitly instead of filling them with narrative.

4. **Analyze business essence**
   - Identify the business model archetype: cycle, white horse/compounder, technology platform, narrative option, capital-operation theme, commodity cost-line trade, or mixed model.
   - Break complex companies into segments before valuing them.
   - Reject simple PE conclusions unless growth, cycle position, moat, and market expectation are analyzed together.

5. **Price the expectation**
   - Estimate what the current price already assumes.
   - Use optimistic/base/pessimistic scenarios with explicit assumptions.
   - For high-growth or technology names, infer embedded success probability instead of relying on a single DCF.
   - For cycles, focus on supply-demand mismatch, cost line, capacity cycle, and downside cushion.

6. **Find the edge**
   - Look for cognitive difference, not just information difference.
   - Prefer opportunities where the market underprices a long-term business change or overprices a consensus narrative.
   - Treat public news as verification or catalyst, not as the investment thesis itself.

7. **Control execution risk**
   - Use technical analysis only for position sizing, timing, stop-loss tolerance, and black-swan defense.
   - Do not claim technical indicators can reliably predict fundamentals.
   - Flag crowded trades, valuation overdraft, expectation peak, and "good industry but bad stock" traps.

8. **Output decision support**
   - Provide conclusion first.
   - Include thesis, valuation range, catalysts, anti-thesis, invalidation conditions, data gaps, and suggested follow-up research.
   - State clearly what requires human judgment.
   - Run the quality-control checklist before final output.

## Output Templates

Read `references/analysis-template.md` for reusable formats:

- **Stock discovery list**: rank candidates by thesis strength, valuation safety, catalyst visibility, and research priority.
- **Single-stock memo**: conclusion, business essence, valuation scenarios, expectation gap, risks, invalidation.
- **Monthly review**: sector rise/fall attribution, missed opportunities, false positives, and process correction.

Read `references/black-swan-template.md` when the user asks for black-swan thinking, anti-consensus analysis, hidden upside/downside, risk-reward asymmetry, or when a stock is heavily driven by consensus expectations.

Read `references/market-research-workflow.md` when starting from an industry theme and building a stock pool.

Read `references/market-regime-rotation-check.md` whenever judging whether a stock is worth buying now, because capital is limited and may be flowing into stronger market themes or sectors.

Read `references/earnings-review-template.md` when analyzing earnings, transcripts, guidance, model updates, or post-results expectation changes.

Read `references/data-source-map.md` when gathering inputs, planning automation, or deciding whether to use web, local notes, financial statements, transcripts, filings, or paid data sources.

Read `references/quality-control-checklist.md` before finalizing any stock analysis or discovery output.

## Hard Rules

- AI drafts; humans sign off. Never let the skill imply automatic trading, automatic approval, or final investment authority.
- Do not treat AI as a price prediction engine.
- Do not replace valuation with qualitative language when current price/market cap and enough financial data are available.
- Do not finalize single-stock analysis without bear/base/bull scenarios. If data is missing, mark **Data gap** and provide a preliminary, explicitly limited view.
- Do not turn public news into an investment thesis without business validation.
- Do not use PE alone to call a stock cheap or expensive.
- Do not ignore valuation simply because the sector narrative is strong.
- Do not answer "worth buying now" without checking market mainline, sector rotation, capital opportunity cost, and whether a stronger theme is absorbing risk capital.
- Do not hide uncertainty. Convert uncertainty into scenarios, probabilities, and invalidation triggers.
- Do not give personalized financial advice. Frame outputs as research support.

## Final QC Before Responding

Before final response, check:

- Did I apply every required reference for this task type?
- Did I separate facts from judgment?
- Did I cite current data source/date where current data matters?
- Did I include bear/base/bull valuation scenarios for single-stock analysis?
- Did I state what current price or market cap already assumes?
- Did I include catalysts, risks, and invalidation conditions?
- Did I check market regime and opportunity cost when judging buy-worthiness?
- Did I avoid deterministic investment advice?

If any answer is "No", revise before final. If the missing item cannot be completed because data is unavailable, include it under **Data gap**.

## Output Anti-Patterns

Bad output:

> The company is a good business, but valuation looks expensive.

Why it fails: lacks current price/market cap, source/date, assumptions, scenario valuation, risk-reward, and invalidation conditions.

Good output pattern:

> At current market cap X as of DATE/SOURCE, the base case assumes revenue A, margin B, and multiple C, implying market cap D. Bear/base/bull scenarios imply downside/upside of E/F/G. The view fails if revenue growth falls below H, margins compress below I, or the market mainline continues to absorb capital into stronger theme J.
