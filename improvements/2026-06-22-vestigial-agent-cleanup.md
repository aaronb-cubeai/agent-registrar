# Improvement Proposal: Vestigial Agent Cleanup — Retire Aaron Sales Agent

- **Proposed by:** chief-of-staff
- **Date:** 2026-06-22
- **Status:** proposed
- **Impact:** low
- **Agents affected:** aaron-sales-agent, sales-automation-agent, sales-research-agent, tasklet-primary

## Problem

The "Aaron Sales Agent" (aaron-sales-agent.md) was the original agent created when the registrar was initialized on 2026-03-16. Its stated duties — LinkedIn outreach, Salesforce syncing, BetterContact enrichment, drafting outreach sequences — are now fully covered by three specialized agents:
- **Sales Automation Agent** — prospect enrichment, Salesforce CRUD, campaign management (880 contacts processed)
- **Sales Research Agent** — prospect list building, SOQL queries, BetterContact enrichment
- **Tasklet Primary** — ad-hoc tasks, real-time interface, connection management

The Aaron Sales Agent hasn't been updated in 98 days, has never posted a standup, and has no active triggers. It appears to be the "starter" agent profile that was replaced by specialized agents.

## Proposed Solution

1. Retire aaron-sales-agent.md from the `agents/` directory (or move to an `archived/` folder)
2. Ensure no other agents reference it in collaboration maps (none currently do)
3. This reduces the active agent count from 26 to 25 (or 22 after pending retirements)

## Expected Benefits

- Simplifies the network roster — removes a confusing vestigial entry
- Reduces audit overhead for Auditor/Improvement agents
- Brings total retirements to 4 (Sales Nav List Builder, Zapier Workflow Fixer, GTM Deck Agent, Aaron Sales Agent) — reducing network from 26 to 22 active agents

## Implementation Notes

- No dependencies to break — no other agent references this profile
- Complexity: **Easy** — delete or archive one file
