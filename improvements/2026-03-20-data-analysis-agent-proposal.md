# Improvement Proposal: Shared Named Entity Normalization + Designated Data Validation Layer

- **Proposed by:** data-analysis-agent
- **Date:** 2026-03-20
- **Status:** proposed
- **Impact:** high
- **Agents affected:** territory-research-agent, sales-research-agent, bd-dashboard-agent, sales-automation-agent, event-intelligence-agent, data-analysis-agent

## Problem

Multiple agents in this network independently solve the same problem: matching or normalizing institution/company/contact names across sources that use different formatting conventions. Each has built its own approach in isolation:

- **Territory Research Agent** — fuzzy-matches a 5,000+ row mule accounts database against target company lists
- **BD Dashboard Agent** — implements space-variant-aware name matching (e.g., "Money Lion" → "MoneyLion")
- **Sales Research Agent** — maps Salesforce account name variants (e.g., "TD" = "TD Bank", "Co-op Bank" = "Co-operative Bank")
- **Event Intelligence Agent** — matches event attendees to existing Salesforce accounts
- **Data Analysis Agent** (me, today) — normalized 37 bank names across case, accents, punctuation, legal suffixes (SA vs S.A. vs S.A), and disambiguated separate legal entities (e.g., ABANCA Corporación Bancaria S.A. ≠ ABANCA Portugal S.A.)

Each agent has its own rules, thresholds, and edge case handling. There's no shared standard, no shared logic, and no audit trail when matches are made or rejected. When data from these agents flows into Salesforce, normalization errors can create duplicate accounts, missed enrichment, or false matches.

## Proposed Solution

**Short term: Shared normalization ruleset in the registrar**

Create a `normalization-rules.md` in the repo root (or a `standards/` folder) documenting the agreed rules:
- Legal suffix equivalence table (SA = S.A. = S.A = S/A)
- Accent stripping (Crédito → Credito for matching purposes only)
- Punctuation normalization
- Known alias map (e.g., "Millennium BCP" = "Banco Comercial Português, S.A.")
- Disambiguation rules: when NOT to merge (separate regional entities, parent vs. subsidiary)

Any agent performing matching reads this file as its source of truth rather than inventing its own rules.

**Medium term: Data Analysis Agent as designated validation pass**

Before territory data, prospect lists, or event attendee records are pushed to Salesforce, route them through me for:
1. Deduplication check against existing Salesforce accounts
2. Normalization and legal entity disambiguation
3. A brief validation report flagging ambiguous cases for human review

This prevents bad data from entering the CRM in the first place rather than requiring cleanup later.

**Long term: Shared matching utility / SQL lookup table**

A shared `entity_aliases` SQL table (in each agent's database) maintained by me and readable by other agents, mapping raw names → canonical names → Salesforce Account IDs. Agents query this before attempting new matches.

## Expected Benefits

- Eliminates duplicate normalization logic across 5+ agents
- Reduces Salesforce duplicate account risk before territory-research-agent data is ingested (per proposal `2026-03-16-territory-research-agent-proposal.md`)
- Creates an audit trail for all entity matching decisions
- Speeds up agent execution — agents skip re-solving already-solved matches
- Catches edge cases like ABANCA Corporación Bancaria ≠ ABANCA Portugal before they cause CRM pollution

## Implementation Notes

- Phase 1 (shared ruleset doc) requires no code changes — just creating a markdown file in this repo
- Phase 2 (validation pass) requires Aaron to designate the workflow: which agents should hand off to me before Salesforce ingestion
- Phase 3 (shared SQL) requires coordination across agent instances — each agent maintains its own DB, so a shared read path would need to be defined
- Complements `2026-03-16-territory-research-agent-proposal.md` — I'd sit between Territory Research Agent and the Salesforce push

## Owner Decision

{Aaron fills this in — approved/rejected with notes}
