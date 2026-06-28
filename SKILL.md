---
name: stock-discovery-analysis
description: Stock discovery and equity analysis workflow for A/H/US stocks, ETFs, themes, sectors, and individual companies. Use when Codex needs to analyze a single stock, review business fundamentals, valuation, industry cycles, catalysts, technical risk controls, monthly review tables, market opportunity cost, or practitioner-informed investment reasoning. Also use to intake and audit candidates produced by stock-discovery-engine, candidate pools, task queues, pending/proposed/approved discovery outputs, or watchlist intake workflows.
---

# Stock Discovery Analysis

## Operating Premise

Use this skill as an **investment research assistant**, not as an autonomous trading system. Provide structured research, assumptions, probability ranges, risk-reward analysis, and invalidation conditions. Do not present deterministic buy/sell instructions.

The agent is allowed and expected to provide **conditional valuation ranges**. It must not provide deterministic buy/sell commands, automated trading decisions, or single-point price targets without assumptions.

Default to the practitioner-informed framework in `references/practitioner-equity-framework.md` when the user asks for stock mining, stock analysis, sector opportunities, valuation gaps, black-swan thinking, monthly review, or experienced investor-style reasoning.

## Research Depth Mode

- If the user explicitly invokes `stock-discovery-analysis`, default to **full research mode**.
- Full research mode means: complete template compliance, evidence separation, gap backfilling, and final QC before response.
- Do not compress into a quick trading-style answer unless the user explicitly asks for a quick version, short version, or high-level view.
- Missing evidence may limit confidence, but it does not justify skipping required sections. Use **Data gap** and **Next research** instead.

## Dual Entry Routing

Choose exactly one entry path before analysis.

### Entry A: Independent Single-Stock Analysis

Use this path when the user directly asks to analyze a stock, asks whether a stock is worth buying/observing/deeper research, or provides one stock or a group of stocks without discovery context.

- Do not require `stock-discovery-engine` context.
- MUST read `references/practitioner-equity-framework.md`, `references/analysis-template.md`, and `references/quality-control-checklist.md` before finalizing.
- Add `references/market-regime-rotation-check.md` when the user asks about worth-buying-now, timing, rotation, or opportunity cost.
- Do not finalize if the required references were not applied.

### Entry B: Candidate Intake

Use this path when the user asks to analyze a candidate from a candidate pool, pending/proposed/approved task, task queue, watchlist intake, or discovery output, including candidates from `stock-discovery-engine`.

- Must apply `references/candidate-intake-template.md`, `references/evidence-grading.md`, `references/analysis-template.md`, and `references/quality-control-checklist.md`.
- Before deep analysis, collect or request: ticker, candidate source, discovery reason, value-chain segment, growth/price mismatch, capital-migration thesis, known data gaps, and discovery-stage review conclusion.
- The final Candidate Intake conclusion must be exactly one of: **建议进入观察池**, **退回候选池**, **建议剔除**, **等待用户确认**.
- Do not finalize if the required references were not applied.

## Mandatory Execution Gates

Before the final answer, complete all applicable gates. Treat these gates as mandatory acceptance criteria, not optional guidance.

1. **Identify task type and entry path**: Entry A independent single-stock analysis, Entry B Candidate Intake, theme research, stock pool discovery, earnings review, sector comparison, valuation check, timing/buy-worthiness, technical risk control, or monthly review.
2. **Load required references**:
   - Single-stock analysis: MUST apply `references/practitioner-equity-framework.md`, `references/analysis-template.md`, and `references/quality-control-checklist.md`.
   - Candidate Intake: MUST apply `references/candidate-intake-template.md`, `references/evidence-grading.md`, `references/analysis-template.md`, and `references/quality-control-checklist.md`.
   - Buy-worthiness or timing: MUST also apply `references/market-regime-rotation-check.md`.
   - Earnings review: MUST also apply `references/earnings-review-template.md`.
   - Black-swan / anti-consensus work: MUST also apply `references/black-swan-template.md`.
   - Theme-to-stock discovery: MUST also apply `references/market-research-workflow.md`.
3. **Collect current data when applicable**: current price, market cap, latest financials, valuation snapshot, and source/date.
4. **Separate facts from judgment**: label current data, user assumptions, market consensus, and AI inference.
5. **Follow the single-stock research sequence when applicable**: company business essence, macro/industry environment, financials/valuation/risks, key observation indicators, role-based debate, then final investment strategy.
6. **Produce required valuation output for single-stock work**: bear/base/bull scenarios, assumptions, implied market cap/value range, upside/downside versus current market cap, and key invalidation triggers.
7. **Check market regime when judging "worth buying now"**: current mainline, stronger competing themes, sector rotation stage, and capital opportunity cost.
8. **For Candidate Intake, grade evidence and separate assumptions**: facts, AI hypotheses, user hypotheses, conflicts, unknowns, and evidence level A/B/C/D.
9. **Backfill key data gaps when possible**: if missing items materially affect valuation, market-regime judgment, or strategy boundary, try to complete them before finalizing rather than only listing them.
10. **Run final QC**: apply the quality-control checklist before responding.

If any gate cannot be completed, do not hide the gap. The final answer MUST include a **Data gap** section explaining what is missing and how that limits confidence.
If required references were not read or applied, the response must not be treated as complete.

## Candidate Intake Hard Rules

- A/B evidence may support core candidate advancement.
- C evidence is auxiliary only.
- D evidence must be labeled as hypothesis and cannot support promotion into watchlist.
- If a candidate mainly depends on C/D evidence, the conclusion must be **退回候选池** or **等待用户确认**.
- Candidate executability means whether it deserves watchlist tracking, not whether it should be bought.
- Explicitly separate: fact layer, AI hypotheses, user hypotheses, conflicts, unknowns, and data gaps.
- Check executability: growth reality, growth persistence, high-frequency verification, why the market has not priced it, catalysts, risk-reward, invalidation, and whether user confirmation is needed.

## Reading Map

- Read `references/analysis-template.md` for the single-stock structure and bear/base/bull output.
- Read `references/practitioner-equity-framework.md` for the default single-stock reasoning standard, business archetypes, valuation discipline, news/catalyst handling, and ending standard.
- Read `references/candidate-intake-template.md` for candidate-source intake, conflict handling, unknowns, executability review, and routing output.
- Read `references/evidence-grading.md` for A/B/C/D evidence rules.
- Read `references/quality-control-checklist.md` before finalizing any output.
- Read `references/market-regime-rotation-check.md` for worth-buying-now, timing, rotation, or opportunity-cost questions.
- Read `references/earnings-review-template.md` for earnings or guidance analysis.
- Read `references/black-swan-template.md` for anti-consensus, hidden downside, or black-swan work.
- Read `references/market-research-workflow.md` when starting from a theme and building a stock pool.
- Read `references/data-source-map.md` when planning data collection or source selection.

## Output Templates
- Use the reusable formats in `references/analysis-template.md` and `references/candidate-intake-template.md`.

## Hard Rules

- AI drafts; humans sign off. Never let the skill imply automatic trading, automatic approval, or final investment authority.
- Do not treat a response as complete unless every required reference for the chosen entry path has been read and applied.
- Automation may call this skill to analyze proposed or approved candidates, but must not automatically write final watchlist status.
- Automation must not modify holdings, trading records, or generate buy/sell actions.
- Candidate Intake outputs are recommendations only; user confirmation is required before a candidate formally enters the watchlist.
- Do not treat AI as a price prediction engine.
- Do not replace valuation with qualitative language when current price/market cap and enough financial data are available.
- Do not finalize single-stock analysis without bear/base/bull scenarios. If data is missing, mark **Data gap** and provide a preliminary, explicitly limited view.
- Do not turn public news into an investment thesis without business validation.
- Do not use PE alone to call a stock cheap or expensive.
- Do not ignore valuation simply because the sector narrative is strong.
- Do not answer "worth buying now" without checking market mainline, sector rotation, capital opportunity cost, and whether a stronger theme is absorbing risk capital.
- Do not hide uncertainty. Convert uncertainty into scenarios, probabilities, and invalidation triggers.
- Do not give personalized financial advice. Frame outputs as research support.
