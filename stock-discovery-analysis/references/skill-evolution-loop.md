# Skill Evolution Loop (Human-Approved Learning)

This skill may **learn and propose**, but must **not auto-edit** its own `SKILL.md` or reference files.

Goal: capture what worked, what failed, and what should change — then wait for human approval before any modification.

## Operating Model

```text
Run analysis
  → capture signals (gaps, corrections, user overrides)
  → append proposal to evolution log
  → periodic synthesis for user review
  → user approves / rejects / edits
  → only then modify skill files
```

This is inspired by self-learning orchestration systems, but with a hard human gate.

## What to Learn From

Capture signals after:

- single-stock analysis
- candidate intake
- earnings review
- monthly review
- user correction ("don't do X", "always check Y")
- repeated **Data gap** on the same field
- route misclassification (wrong depth or wrong template)

Do **not** learn from:

- one-off typos
- unavailable external data the user never cared about
- contradictory user preferences without clarification

## Proposal Types

| Type | Example |
|---|---|
| `routing` | "timing questions should always load market-regime-rotation-check" |
| `data_source` | "A-share revenue should default to eastmoney + cninfo" |
| `template` | "deep mode needs explicit AI researchability rating" |
| `qc_gate` | "missing facilitator verdict should fail QC" |
| `wording` | "replace 'buy' language with 'attractive/watchlist'" |
| `deprecate` | "remove unused section causing token waste" |

## Storage Layout

Preferred local workspace:

```text
~/Documents/investment-research/skill-evolution/
├── proposals/
│   └── YYYY-MM-DD-{slug}.md
├── ledger.jsonl
└── approved/
    └── YYYY-MM-DD-{slug}.md
```

If the folder does not exist, offer to create it; do not silently invent prior proposals.

## Ledger Entry Format

Append one JSON line per meaningful signal:

```json
{
  "date": "2026-07-11",
  "task": "single_stock",
  "ticker": "XXXX",
  "depth": "deep",
  "route_used": ["skill-router", "analysis-template", "parallel-analyst-reports"],
  "signal_type": "user_correction",
  "observation": "User said A-share sentiment should never be primary evidence",
  "proposal_type": "qc_gate",
  "proposed_change": "Add hard rule: sentiment report cannot upgrade final classification alone",
  "confidence": "high",
  "status": "pending"
}
```

## Proposal File Template

When a signal is strong enough, also write a human-readable proposal:

```markdown
# Skill Evolution Proposal: {title}

- Date:
- Status: pending / approved / rejected
- Trigger session:
- Problem observed:
- Evidence:
- Proposed change:
- Files affected:
- Expected benefit:
- Risk / tradeoff:
- User decision: approve / reject / revise
```

## When to Propose

Propose a skill change when any of these is true:

1. Same correction appears **2+ times**.
2. Same **Data gap** blocks conclusions repeatedly for a market/task type.
3. User explicitly asks to change workflow.
4. QC failure pattern repeats across sessions.
5. A route clearly wasted tokens without improving output quality.

Otherwise, log lightly in `ledger.jsonl` only.

## End-of-Session Behavior

After substantial analysis work, append a short section when relevant:

```markdown
## Skill Evolution Notes
- Route used:
- What worked:
- What was missing:
- Proposed skill update (if any):
- Status: pending user review
```

If there is no meaningful signal, omit this section.

## Periodic Synthesis (Weekly / Monthly)

When user asks for skill review, synthesize pending proposals into:

1. **High-confidence changes** — recommend approval
2. **Medium-confidence changes** — need user judgment
3. **Rejected patterns** — do not propose again
4. **Token savings opportunities** — routing/template compression

Output must be action-oriented:

```markdown
# Skill Evolution Review

## Recommend Approve
- ...

## Needs Your Decision
- ...

## Do Not Change
- ...

## Next Step
Reply with: approve {id}, reject {id}, or revise {id}: ...
```

## Hard Rules

- Never modify `SKILL.md` or `references/*.md` automatically from learning signals.
- Never mark a proposal `approved` without explicit user confirmation.
- Approved changes should be small, testable, and reversible.
- Keep a changelog note inside the approved proposal file.
- Learning improves **process**, not investment conclusions themselves.
- Do not store secrets, account info, or trade execution details in evolution logs unless user explicitly wants them there.

## Relationship to Decision Memory

| Decision Memory | Skill Evolution |
|---|---|
| Ticker-specific thesis history | Framework/process improvements |
| "Were we right on NVDA?" | "Should deep mode always load X?" |
| Updated per stock | Updated per workflow pattern |
| Human-approved optional | Human-approved mandatory |

Use both, but do not merge them into one file.
