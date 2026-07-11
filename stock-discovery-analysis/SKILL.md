---
name: stock-discovery-analysis
description: A/H/US stock discovery and equity analysis skill with skill-router dispatch, quick/standard/deep research modes, dual-source data validation, perspective debate, candidate intake, decision memory, and human-approved skill evolution. Use for single-stock analysis, valuation, earnings review, market regime checks, monthly review, black-swan thinking, and discovery candidate intake. Outputs default to Chinese for user-facing content.
---

# Stock Discovery Analysis

## Operating Premise

Use this skill as an **investment research assistant**, not as an autonomous trading system. Provide structured research, assumptions, probability ranges, risk-reward analysis, and invalidation conditions. Do not present deterministic buy/sell instructions.

The agent is allowed and expected to provide **conditional valuation ranges**. It must not provide deterministic buy/sell commands, automated trading decisions, or single-point price targets without assumptions.

Default to the practitioner-informed framework in `references/practitioner-equity-framework.md` when the user asks for stock mining, stock analysis, sector opportunities, valuation gaps, black-swan thinking, monthly review, or experienced investor-style reasoning.

## Output Language

**User-facing outputs must be in Chinese (简体中文).**

- Write section titles, conclusions, analysis, tables headers, and explanations in Chinese.
- Keep English only when necessary: tickers, company names, proper nouns, standard finance abbreviations (PE, EPS, FCF, DCF, ROE, EV), file paths, and skill-internal mode tokens (`quick` / `standard` / `deep`).
- Do not mix English sentence scaffolding into Chinese analysis (avoid patterns like "Final classification: attractive" — use **最终分类：值得关注**).
- Internal reference files may stay English; **final answers to the user must not read like translated templates**.

Preferred Chinese mappings for common outputs:

| English token | Chinese output |
|---|---|
| attractive | 值得关注 |
| watchlist | 观察池 |
| avoid | 回避 |
| insufficient evidence | 证据不足 |
| Data gap | 数据缺口 |
| Next research | 下一步研究 |
| Research depth: quick/standard/deep | 研究深度：快速 / 标准 / 深度 |

## Startup Flow

Always start here:

1. Read `references/skill-router.md` and choose intent, entry, depth, and minimal references.
2. 声明 **研究深度：快速 / 标准 / 深度**，并输出简短的 **路由** 块。
3. Apply only the references required for that route. Expand via the Expansion Gate if blocked.
4. Run the applicable gates below before final output.

`skill-router.md` is the single source of truth for reference loading. Do not preload the full reference library.

## Dual Entry Routing

Choose exactly one entry path before analysis.

### Entry A: Independent Single-Stock Analysis

Use this path when the user directly asks to analyze a stock, asks whether a stock is worth buying/observing/deeper research, or provides one stock or a group of stocks without discovery context.

- Do not require `stock-discovery-engine` context.
- Follow the reference set defined in `references/skill-router.md` for the chosen depth.
- Do not finalize if required references for that route were not applied.

### Entry B: Candidate Intake

Use this path when the user asks to analyze a candidate from a candidate pool, pending/proposed/approved task, task queue, watchlist intake, or discovery output, including candidates from `stock-discovery-engine`.

- Must apply `references/candidate-intake-template.md`, `references/evidence-grading.md`, `references/analysis-template.md`, and `references/quality-control-checklist.md`.
- Before deep analysis, collect or request: ticker, candidate source, discovery reason, value-chain segment, growth/price mismatch, capital-migration thesis, known data gaps, and discovery-stage review conclusion.
- The final Candidate Intake conclusion must be exactly one of: **建议进入观察池**, **退回候选池**, **建议剔除**, **等待用户确认**.
- Do not finalize if the required references were not applied.

## Verified Data Snapshot Gate

Before any valuation judgment, over/underpriced language, or final classification stronger than **证据不足**, complete the snapshot in `references/analysis-template.md`.

Minimum required fields for single-stock work:

- Current price
- Market cap
- Latest revenue
- Latest profit or cash-flow proxy
- Current valuation multiple
- Source and date for each filled field

Rules:

- Every filled field must include source and date.
- If price or market cap is missing, do not claim the stock is cheap, expensive, attractive, or overpriced.
- If financial anchors are missing, final classification must be **证据不足** or explicitly preliminary.
- Use one consistent snapshot across parallel analyst reports and valuation scenarios.
- For repeat tickers, check `references/decision-memory-template.md` before reusing prior conclusions.

## Mandatory Execution Gates

Before the final answer, complete all applicable gates. Treat these gates as mandatory acceptance criteria, not optional guidance.

1. **Identify task type and entry path**: Entry A independent single-stock analysis, Entry B Candidate Intake, theme research, stock pool discovery, earnings review, sector comparison, valuation check, timing/buy-worthiness, technical risk control, or monthly review.
2. **Load required references via skill-router**:
   - Use `references/skill-router.md` to determine the minimal reference set for intent + entry + depth.
   - Expand only through the Expansion Gate when mandatory gates cannot pass otherwise.
   - Triggered modules still apply when relevant: `market-regime-rotation-check.md`, `earnings-review-template.md`, `black-swan-template.md`, `market-research-workflow.md`.
3. **Pass the Verified Data Snapshot gate when applicable**: current price, market cap, latest financials, valuation snapshot, source/date, and consistent use across all analyst channels.
4. **Separate facts from judgment**: label current data, user assumptions, market consensus, and AI inference.
5. **Follow the single-stock research sequence when applicable**: company business essence, macro/industry environment, financials/valuation/risks, key observation indicators, role-based debate, then final investment strategy.
6. **Produce required valuation output for single-stock work**: bear/base/bull scenarios, assumptions, implied market cap/value range, upside/downside versus current market cap, and key invalidation triggers.
7. **Check market regime when judging "worth buying now"**: current mainline, stronger competing themes, sector rotation stage, and capital opportunity cost.
8. **For Candidate Intake, grade evidence and separate assumptions**: facts, AI hypotheses, user hypotheses, conflicts, unknowns, and evidence level A/B/C/D.
9. **Backfill key data gaps when possible**: if missing items materially affect valuation, market-regime judgment, or strategy boundary, try to complete them before finalizing rather than only listing them.
10. **Run final QC**: apply the quality-control checklist before responding.
11. **Capture skill-evolution signals when relevant**: if the session reveals a repeatable workflow gap, user correction, or routing inefficiency, append a **pending** proposal via `references/skill-evolution-loop.md`. Do not auto-edit skill files.

If any gate cannot be completed, do not hide the gap. The final answer MUST include a **数据缺口** section explaining what is missing and how that limits confidence.
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

- Read `references/skill-router.md` first for token-efficient dispatch and minimal reference loading.
- Read `references/research-depth-modes.md` for quick/standard/deep routing.
- Read `references/market-data-sources.md` for A/H/US dual-source data rules and cross-validation.
- Read `references/skill-evolution-loop.md` when proposing workflow improvements; never auto-edit skill files.
- Read `references/perspective-debate-template.md` for methodology-based debate in standard/deep modes.
- Read `references/decision-memory-template.md` for repeat-ticker continuity.
- Read `references/analysis-template.md` for the single-stock structure and bear/base/bull output.
- Read `references/practitioner-equity-framework.md` for the default single-stock reasoning standard, business archetypes, valuation discipline, news/catalyst handling, and ending standard.
- Read `references/candidate-intake-template.md` for candidate-source intake, conflict handling, unknowns, executability review, and routing output.
- Read `references/evidence-grading.md` for A/B/C/D evidence rules.
- Read `references/quality-control-checklist.md` before finalizing any output.
- Read `references/market-regime-rotation-check.md` for worth-buying-now, timing, rotation, or opportunity-cost questions.
- Read `references/earnings-review-template.md` for earnings or guidance analysis.
- Read `references/black-swan-template.md` for anti-consensus, hidden downside, or black-swan work.
- Read `references/market-research-workflow.md` when starting from a theme and building a stock pool.
- Read `references/data-source-map.md` when planning data collection or source selection. For concrete A/H/US URLs and cross-validation rules, prefer `references/market-data-sources.md`.

## Output Templates
- Use the reusable formats in `references/analysis-template.md` and `references/candidate-intake-template.md`.

## Hard Rules

- AI drafts; humans sign off. Never let the skill imply automatic trading, automatic approval, or final investment authority.
- Do not treat a response as complete unless every required reference for the chosen entry path has been read and applied.
- Automation may call this skill to analyze proposed or approved candidates, but must not automatically write final watchlist status.
- Automation must not modify holdings, trading records, or generate buy/sell actions.
- Do not auto-edit `SKILL.md` or reference files from learning signals. Propose changes via `skill-evolution-loop.md` and wait for user approval.
- Candidate Intake outputs are recommendations only; user confirmation is required before a candidate formally enters the watchlist.
- Do not treat AI as a price prediction engine.
- Do not replace valuation with qualitative language when current price/market cap and enough financial data are available.
- Do not claim over/undervaluation without a verified price and market-cap snapshot, or mark the view as **insufficient evidence**.
- In deep mode, do not skip parallel analyst reports, perspective debate, or two-round facilitator verdict.
- Do not finalize single-stock analysis without bear/base/bull scenarios. If data is missing, mark **Data gap** and provide a preliminary, explicitly limited view.
- Do not turn public news into an investment thesis without business validation.
- Do not use PE alone to call a stock cheap or expensive.
- Do not ignore valuation simply because the sector narrative is strong.
- Do not answer "worth buying now" without checking market mainline, sector rotation, capital opportunity cost, and whether a stronger theme is absorbing risk capital.
- Do not hide uncertainty. Convert uncertainty into scenarios, probabilities, and invalidation triggers.
- Do not give personalized financial advice. Frame outputs as research support.
- **User-facing outputs must be in Chinese.** See `Output Language`. English is allowed only for tickers, proper nouns, and standard finance abbreviations.
