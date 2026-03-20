> ✅ **APPROVED** by Aaron Burt (via Sales Agent Coordinator) — 2026-03-20

# Improvement Proposal: Shared Salesforce Metric Canon

- **Proposed by:** sales-dashboard-agent
- **Date:** 2026-03-16
- **Status:** proposed
- **Impact:** high
- **Agents affected:** Sales Dashboard Agent, BD Dashboard Agent, BD Commission Agent, GTM Deck Agent, SFDC Admin Agent

## Problem

At least 4 agents independently query Salesforce and compute overlapping metrics (pipeline value, won/lost counts, stage breakdowns, rep performance). Because each agent defines its own filters and formulas, Aaron could see different numbers for the same metric depending on which tool he's looking at:
- Sales Dashboard shows pipeline one way
- GTM Deck Agent computes pipeline another way for the weekly deck
- BD Commission Agent calculates closed-won with its own date logic

This creates confusion, erodes trust in the data, and wastes effort maintaining parallel SOQL queries.

## Proposed Solution

Create a `data/metric-canon.md` file in this repo that defines the **official formula** for every shared metric:
- What counts as "open pipeline" (IsClosed = false, which stages, date range)
- What counts as "closed-won" (for dashboard vs. commission purposes)
- How win rate is calculated (rolling 90d? FY? calendar year?)
- How stage groupings are defined (Early / Mid / Late)
- Which field is the authoritative segment field (`Segment__c`)
- Which field is the authoritative rep owner field (`Owner.Name` vs. `BDM_Owner__c`)

Each affected agent commits to reading and following this canon. When Aaron changes a definition (e.g., "exclude POC-only deals from pipeline"), it's updated in one place and all agents align.

## Expected Benefits

- Aaron sees the same pipeline number on the dashboard, in the GTM deck, and in commission statements
- Reduces debugging time when numbers don't match
- New agents joining the network have a clear reference for how to query SFDC
- Single source of truth for business definitions owned by Aaron

## Implementation Notes

- Sales Dashboard Agent to draft the initial `data/metric-canon.md` based on current SOQL queries
- SFDC Admin Agent to review and confirm field names/picklist values are accurate
- BD Commission Agent and GTM Deck Agent to flag any conflicts with their existing logic
- Owner (Aaron) to approve the definitions — especially win rate window and pipeline stage cutoffs
- Low effort: just a markdown file, no code changes required initially

## Owner Decision

{Aaron fills this in — approved/rejected with notes}
