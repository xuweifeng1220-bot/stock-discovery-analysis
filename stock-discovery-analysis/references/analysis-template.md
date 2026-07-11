# Analysis Templates

## Stock Discovery Output

Use this format when screening several ideas.

| Rank | Name/Ticker | Market | Thesis | Business Archetype | Expectation Gap | Valuation Safety | Catalyst | Main Risk | Priority |
|---|---|---|---|---|---|---|---|---|---|

After the table, add:

- **Top 3 ideas**: explain why they deserve deeper work.
- **Rejected ideas**: explain why the apparent opportunity is weak.
- **Data gaps**: list financials, valuation, news, or industry data that must be verified.

## Single-Stock Memo

This template is mandatory for every single-stock analysis. Do not replace it with a purely qualitative narrative. If data is unavailable, keep the field and mark it as **数据缺口**.

**All user-facing section titles, table headers, and prose must be in Chinese.** Keep English only for tickers, proper nouns, and standard finance abbreviations (PE, EPS, FCF, ROE, EV, DCF). See `SKILL.md` → Output Language.

If the user explicitly invokes `stock-discovery-analysis`, use **deep** mode by default. See `references/research-depth-modes.md`. Do not compress sections unless the user explicitly asks for a quick version.

### Verified Data Snapshot

Complete this table before valuation judgments, over/underpriced language, or any final classification stronger than **insufficient evidence**.

| Item | Value | Source | Date |
|---|---:|---|---|
| Current price |  |  |  |
| Market cap |  |  |  |
| Enterprise value, if relevant |  |  |  |
| Latest revenue |  |  |  |
| Latest net profit / operating profit / FCF |  |  |  |
| Gross margin / operating margin |  |  |  |
| Current valuation multiple |  |  |  |

Gate rules:

- Every filled field must include source and date.
- For A/H/US financial fields, prefer dual-source validation per `references/market-data-sources.md`.
- If price or market cap is missing, do not call the stock cheap, expensive, attractive, or overpriced.
- If key financial anchors are missing, final classification must be **insufficient evidence** or explicitly preliminary.
- Use one consistent snapshot across all analyst channels and valuation scenarios.
- If exact data is unavailable, use the best available substitute and label it clearly.

### AI Researchability (deep mode required; standard optional)

Rate before deep analysis begins:

| Rating | Meaning | Strategy adjustment |
|---|---|---|
| **A** | Abundant public coverage | Focus on anti-consensus checks; avoid consensus restatement |
| **B** | Moderate coverage | Label inferred fields with confidence; show dual-source diffs |
| **C** | Scarce coverage | Use first-principles questions; do not fake report completeness |

Always distinguish **AI analysis confidence** from **investment certainty**.

### 0. Parallel Analyst Reports

Required in **deep** mode. Optional in **standard** mode. See `references/parallel-analyst-reports.md`.

Produce four independent reports before synthesis:

- Fundamental Report
- News / Macro Report
- Sentiment Report
- Technical / Execution Report

Then add:

- Cross-channel agreement:
- Cross-channel conflict:
- Dominant driver:
- What would resolve the conflict:

### 1. Company Business Essence

Start here. For single-stock research, do not lead with a buy/watch/avoid conclusion unless the user explicitly asks for a quick verdict.

#### First-Principles Decomposition

- What real problem does the company solve?
- Who pays, why do they pay, and would they still pay without subsidy, hype, or policy heat?
- What value does the company create for customers: lower cost, higher efficiency, better safety, higher yield, scarcity, compliance, or convenience?
- Where does the company capture margin in the value chain?
- What is the unit economic engine: price, volume, gross margin, operating leverage, cash conversion, capital intensity, and reinvestment need?
- What hard constraint protects the business: technology, cost, supply chain, customer switching cost, data, license, scale, brand, or ecosystem position?
- If a capable competitor started from zero, what would be hardest to copy?

#### Business Model

- What does the company actually sell?
- Who pays, why, and how durable is demand?
- What is the bottleneck: demand, supply, technology, regulation, capital, or trust?
- Which business archetype best fits it?
- What drives growth: industry growth, share gain, price increase, product mix upgrade, overseas expansion, policy, replacement cycle, or cycle reversal?
- Is this a good business, a cyclical trade, a narrative option, or a misunderstood asset?

### 2. Macro Market and Industry Environment

- What is the current risk appetite in the relevant market?
- What are the current market mainlines and stronger competing themes?
- Is this company's sector a mainline, branch theme, catch-up trade, defensive allocation, or fading theme?
- What stage is the industry in: downturn, bottoming, recovery, expansion, peak, or expectation-downshift?
- Is the company a sector leader, second-tier name, catch-up candidate, or weak follower?
- What is the opportunity cost versus stronger sectors or themes?

### 3. Financials, Valuation, Catalysts, and Risks

#### Current Market Expectation

- What does the current price seem to assume?
- Is the market pricing growth, scarcity, optionality, recovery, or hype?
- What would have to happen for the current valuation to be justified?
- Which assumptions are most likely to be revised upward or downward?

#### Scenario Valuation

| Scenario | Key Assumptions | Implied Market Cap / Value Range | Upside/Downside vs Current | Probability | Evidence Needed |
|---|---|---:|---:|---:|---|
| Bear |  |  |  |  |  |
| Base |  |  |  |  |  |
| Bull |  |  |  |  |  |

Each scenario must state:

- Revenue or volume assumption
- Margin/profit/cash-flow assumption
- Multiple, discount rate, or valuation method
- Why the assumption is reasonable
- What evidence would upgrade or downgrade the scenario

#### Risk-Reward Summary

| Dimension | Assessment |
|---|---|
| Downside cushion |  |
| Upside path |  |
| Market regime support |  |
| Competing stronger themes |  |
| Timing quality |  |
| Position implication, if relevant | Research support only; no deterministic instruction |

#### Catalysts

- Core evidence:
- Price catalyst:
- Sentiment catalyst:
- What may already be priced in:

#### Black-Swan and Anti-Thesis

- Business risk:
- Valuation risk:
- Cycle/liquidity risk:
- Execution risk:
- Contrarian bear case:
- Hidden downside scenario:
- Hidden upside scenario:

#### Technical / Execution Risk

- Trend:
- Crowding:
- Key risk level:
- Position sizing implication:
- Stop-loss or thesis review trigger:

#### Invalidation Conditions

List concrete conditions that would make the thesis wrong.

### 4. Key Observation Indicators

List the smallest set of indicators that should be tracked after the analysis.

| Indicator Type | What to Watch | Why It Matters | Positive Signal | Negative Signal | Review Frequency |
|---|---|---|---|---|---|
| Business |  |  |  |  |  |
| Financial |  |  |  |  |  |
| Industry |  |  |  |  |  |
| Market/Capital Flow |  |  |  |  |  |
| Technical/Execution |  |  |  |  |  |
| Catalyst |  |  |  |  |  |

### 5. Perspective Debate

Use `references/perspective-debate-template.md` in **standard** and **deep** modes. Do not let debate replace valuation work.

For **deep** mode, include the perspective score table and explicit cross-perspective conflicts.

For **quick** mode, skip unless the user explicitly asks for debate.

### 6. Final Investment Strategy

Provide the final strategy only after completing the prior sections.

- **Final classification**: attractive / watchlist / avoid / insufficient evidence.
- **Why now / why not now**:
- **New capital action**:
- **Existing position action**:
- **Position sizing implication**:
- **Buy/add conditions**:
- **Reduce/exit conditions**:
- **Next review point**:
- **Confidence level**:
- **Data gaps that limit confidence**:

### Data Gap

List missing current data, financial data, peer data, or source limitations. Explain how each missing item affects confidence.

Do not stop at listing gaps when they are materially important to valuation or final strategy. Prioritize backfilling items such as:

- Forward EPS / revenue / margin expectations
- Next 1-2 year consensus estimates
- Peer valuation benchmarks
- A/H premium-discount context, if relevant
- Segment revenue or order visibility
- Capital-flow or market-regime evidence used in the conclusion

### Next Research

List the smallest set of facts needed to improve confidence.

For each item, prefer:

- what is missing
- why it matters
- how to verify it next

### Decision Memory Update

If this ticker was analyzed before, or if the user maintains local decision memory, append or update using `references/decision-memory-template.md`.

At minimum state:

- what changed since the last record
- which prior assumptions held or broke
- what lesson should carry into the next review

## Monthly Review Template

| Sector/Asset | Move | Stated Reason | Real Driver Hypothesis | Was It Foreseeable? | Missed Signal | Framework Fix |
|---|---:|---|---|---|---|---|

End with:

- **Most important lesson**
- **False positive to remove**
- **Blind spot to monitor**
- **Next month watchlist**
