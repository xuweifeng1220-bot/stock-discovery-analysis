# Data Source Map

Use this map when planning inputs for stock discovery, single-stock analysis, earnings review, or future automation.

## Source Hierarchy

Prefer sources in this order:

1. **Primary filings and official releases**
   - Annual reports
   - Quarterly reports
   - Prospectuses
   - Investor presentations
   - Exchange filings
   - Company press releases

2. **Management and event transcripts**
   - Earnings calls
   - Investor days
   - Conference presentations
   - Q&A transcripts

3. **Market and valuation data**
   - Price
   - Market cap
   - Enterprise value
   - Revenue, earnings, cash flow
   - Multiples
   - Peer data

4. **Industry and value-chain evidence**
   - Industry reports
   - Production/capacity data
   - Commodity prices
   - Import/export data
   - Policy documents
   - Customer/order evidence

5. **News and event intelligence**
   - Real-time news
   - Regulatory changes
   - Product announcements
   - Competitor actions

6. **User-maintained notes and local files**
   - Local notes / personal knowledge base
   - Local research folders
   - Meeting notes
   - Manual trade review tables
   - Screenshots and charts

7. **Paid or enterprise data vendors when available**
   - Examples include financial data terminals, market data platforms, transcript providers, research databases, and company document repositories.
   - Newswire services

## Data Quality Labels

Label important evidence:

- **A: primary and current**
- **B: reputable secondary**
- **C: useful but needs verification**
- **D: rumor/noisy**
- **Unknown: source not available**

## Automation Boundary

AI may:

- Gather and summarize data
- Compare sources
- Build tables
- Mark missing evidence
- Draft memos
- Propose assumptions

AI must not:

- Invent unavailable data
- Treat vendor data as available without access
- Execute trades
- Approve investment decisions
- Hide source uncertainty

## Minimal Input Set by Task

### Theme Discovery

- Theme definition
- Market scope
- Value-chain evidence
- Candidate company list
- Current valuation snapshot
- Catalysts and risks

### Single Stock

- Ticker and market
- Current price/market cap
- Latest financials
- Segment data
- Peer group
- Recent news/catalysts
- User's current thesis or concern

### Earnings Review

- Latest report
- Prior expectations or consensus
- Earnings call transcript
- Guidance
- Price reaction
- Prior model assumptions

### Monthly Review

- Sector/asset performance
- Major winners and losers
- Key news/events
- Prior watchlist
- User's actual trades if available

## Output Rule

If required data is unavailable, do not stop the analysis. Continue with a labeled preliminary view and list the smallest evidence set needed to improve confidence.
