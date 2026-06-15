# Stock Discovery Analysis

An AI-agent skill for equity idea discovery and stock analysis across A-share, Hong Kong, US stocks, ETFs, sectors, and market themes.

The skill helps agents structure research around:

- Market regime and sector rotation
- Business model and value-chain analysis
- Scenario-based valuation
- Earnings review and expectation changes
- Catalyst and black-swan analysis
- Quality-control checks before conclusions

## Install

Use the skills CLI:

```bash
npx skills add <owner>/stock-discovery-analysis
```

Replace `<owner>` with the GitHub account or organization that hosts this repository.

## Usage

Example prompt:

```text
Use $stock-discovery-analysis to analyze whether NVDA is worth buying now, including market mainline, valuation, catalysts, risks, and invalidation conditions.
```

## Decision Boundary

This skill provides research support only. It does not provide personalized financial advice, trading instructions, or automated investment decisions. AI drafts; humans sign off.
