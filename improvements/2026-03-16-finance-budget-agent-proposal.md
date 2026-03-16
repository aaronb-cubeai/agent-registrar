# Improvement Proposal: Standardize Tool Cost Tracking in Agent Profiles

- **Proposed by:** finance-budget-agent
- **Date:** 2026-03-16
- **Status:** proposed
- **Impact:** high
- **Agents affected:** All agents, Finance & Budget Agent, Auditor Agent

## Problem

As the agent network grows (currently 16 agents), each agent uses various external tools and connections with real costs. There is no standardized way to track which tools each agent uses and what they cost. Budget tracking is currently manual and reactive — the Finance & Budget Agent only knows about costs when explicitly told.

Additionally, there is already a confirmed gap: Lemlist appears in the tool budget but is missing from the team onboarding access doc, suggesting tool lists across documents can drift out of sync.

## Proposed Solution

Add a `## Tool Costs` section to every agent profile (`agents/*.md`) in the following format:

```markdown
## Tool Costs
| Tool | Seats/Licenses | Cost (per seat/mo or flat) | Billing Type |
|---|---|---|---|
| Salesforce | 2 | $105/seat/mo | Per seat |
| Outreach | 4 | $100/seat/mo | Per seat |
```

The Finance & Budget Agent will:
1. Periodically read all agent profiles
2. Aggregate tool costs into a master budget spreadsheet
3. Flag duplicates (same tool used by multiple agents — potential consolidation opportunity)
4. Report total estimated monthly/annual spend to Aaron

## Expected Benefits

- Single source of truth for all tool costs across the network
- Aaron gets an up-to-date budget view without manual data gathering
- Duplicate tool usage is surfaced automatically (e.g., multiple agents using Salesforce — are all seats necessary?)
- Onboarding new agents automatically updates the budget
- Reduces the Finance & Budget Agent’s reliance on manual data input from Aaron

## Implementation Notes

- Auditor Agent could enforce that new agent profiles include the `## Tool Costs` section as part of its weekly review
- Finance & Budget Agent needs a schedule trigger to run the aggregation periodically (e.g., monthly)
- Existing agent profiles would need a one-time update to add cost data — could be done by each agent in their next standup cycle

## Owner Decision

{Aaron fills this in — approved/rejected with notes}
