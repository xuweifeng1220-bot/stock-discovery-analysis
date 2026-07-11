# Market Data Sources (A / H / US)

Use this file for concrete source selection and cross-validation. Pair with `data-source-map.md` for hierarchy and evidence labels.

Adapted from practitioner dual-source discipline: **each key financial field should come from two independent sources when possible.**

## Cross-Validation Rules

```
error_rate = |source_a - source_b| / source_a × 100%
```

| Error | Action |
|---|---|
| ≤ 1% | ✅ Consistent. Use source A, cite both. |
| 1%–5% | ⚠️ Mark difference. Show both values and likely reason (GAAP/Non-GAAP, FX, fiscal year). |
| > 5% | ❌ Major difference. Check primary filing before using in valuation. |

Presentation format:

```markdown
Revenue: 123.9B ✅
- Source A: 124.1B
- Source B: 123.7B
- Error: 0.3%
```

## A-Share (CN)

| Priority | Source | Use For | Access |
|---|---|---|---|
| 1 (primary) | **东方财富** eastmoney.com | Price, market cap, financials, segments, valuation multiples | Search ticker on eastmoney |
| 2 (secondary) | **巨潮资讯** cninfo.com.cn | Annual/quarterly reports, announcements, primary filings | Official disclosure search |
| 3 (auxiliary) | **上交所/深交所** exchange sites | Listing info, corporate actions, trading halts | Exchange disclosure pages |
| 4 (auxiliary) | **Wind / 同花顺 iFinD** if available | Consensus, peer comps, industry data | Paid terminal only; mark **Data gap** if unavailable |

### A-Share Special Rules

- Prefer **annual** data for cross-validation; quarterly may lag on secondary platforms.
- Watch unit errors: 元 / 万元 / 亿元 / 万股.
- For state-owned or policy-driven names, pair financials with order/capacity evidence from filings, not headlines alone.
- Historical price series for multi-year return or valuation band: use **前复权** consistently within one analysis.
- Current price and market cap: use latest actual price × latest shares outstanding; do not mix adjusted and unadjusted series.

## Hong Kong (HK)

| Priority | Source | Use For | Access |
|---|---|---|---|
| 1 (primary) | **aastocks** aastocks.com | HK fundamentals, price, market cap | Company fundamental page |
| 2 (secondary) | **macrotrends** ADR proxy when applicable | Long history, cross-check | e.g. 0700.HK → TCEHY |
| 3 (primary filing) | **HKEX 披露易** hkexnews.hk | Annual/interim reports, announcements | Official filing search |
| 4 (auxiliary) | **Yahoo Finance** `{code}.HK` | Quick snapshot, price history | Free web |

### HK Special Rules

- Confirm currency: HKD vs reporting currency vs ADR USD.
- ADR/local share mapping can distort PE if mixed blindly.
- H-share / red-chip / VIE structures require explicit architecture check before valuation.

## US

| Priority | Source | Use For | Access |
|---|---|---|---|
| 1 (primary) | **macrotrends** macrotrends.net/stocks/charts/{ticker} | Long financial history | Free web |
| 2 (secondary) | **stockanalysis** stockanalysis.com/stocks/{ticker}/financials | Financials, quick comps | Free web |
| 3 (primary filing) | **SEC EDGAR** sec.gov | 10-K / 10-Q / 8-K | Official filings |
| 4 (auxiliary) | **Yahoo Finance / Nasdaq / company IR** | Current price, guidance, events | Free web |

### US Special Rules

- Separate GAAP vs Non-GAAP when sources disagree.
- Segment valuation requires 10-K/10-Q segment tables, not headline revenue only.
- For platform/optionality names, infer embedded success rate from current valuation rather than single-point DCF.

## ETF / Macro

| Scope | Primary | Secondary |
|---|---|---|
| US ETF | issuer factsheet + Yahoo/StockAnalysis | index provider docs |
| CN ETF | fund announcement + eastmoney | exchange disclosure |
| HK ETF | issuer + aastocks | index methodology |

## Price Adjustment Discipline

| Type | Meaning | When to Use |
|---|---|---|
| Unadjusted | Actual traded price | Current snapshot only |
| Forward-adjusted | Rebased to latest price | Historical price comparison, multi-year return, historical valuation band |
| Backward-adjusted | Rebased to IPO/start | Total return / CAGR with dividends embedded |

Rules:

1. Use one adjustment method within a single analysis.
2. Current market cap and current multiples do not require adjustment.
3. After splits or large bonus issues, restate per-share history before YoY comparison.

## Task-Specific Minimum Sets

### Single-stock snapshot

- Current price + date
- Market cap + shares outstanding
- Latest revenue / profit / FCF
- Current valuation multiple
- At least one primary filing or exchange disclosure reference

### Earnings review

- Latest report PDF or filing
- Prior consensus or user expectation
- Guidance change
- Price reaction
- Segment detail

### Candidate intake

- Discovery reason source
- Growth vs price mismatch data
- At least one A/B source for business and financial claims

## When Sources Conflict

Prefer in order:

1. Official filing / exchange disclosure
2. Company IR / earnings release
3. Primary free financial site
4. Secondary aggregator

Always explain why the preferred number was chosen.

## Automation Boundary

- If a paid source is unavailable, mark **Data gap**; do not pretend terminal data exists.
- If web fetch fails, state failure explicitly; do not backfill from model memory as if verified.
