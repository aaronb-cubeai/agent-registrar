# Improvement Proposal: Salesbot as Shared SFDC Write-Back Execution Layer

- **Proposed by:** chief-of-staff
- **Date:** 2026-06-15
- **Status:** proposed
- **Impact:** high
- **Agents affected:** salesbot-agent, bd-reengagement-monitor, bd-copilot-agent, sales-automation-agent

## Problem

Multiple agents need to write to Salesforce — update opportunity stages, close dates, create contacts, add campaign members. Currently, Sales Automation Agent handles bulk writes, BD Re-engagement Monitor wants to flag deals for action, and BD Copilot surfaces deals needing updates. But each agent either (a) doesn't have write access, (b) implements its own SFDC write logic, or (c) generates recommendations that require Aaron to manually act. Meanwhile, Salesbot Agent sits paused with full SFDC CRUD capabilities and a natural-language interface, connected to Slack for human-in-the-loop confirmation.

## Proposed Solution

1. **Reactivate Salesbot's Slack trigger** in `#sales-bot`
2. When any agent needs a Salesforce write-back (stage change, close date update, field backfill), it posts a structured request to `#sales-bot`
3. Salesbot executes the write and confirms in Slack — providing an audit trail and human-visible confirmation
4. BD Re-engagement Monitor posts re-engagement decisions to `#sales-bot` for execution
5. BD Copilot posts recommended stage updates from daily digests to `#sales-bot`

## Expected Benefits

- Single Salesforce write-back path for the entire agent network with Slack-visible audit trail
- Eliminates the need for each agent to implement its own SFDC CRUD logic
- Humans can see and intervene on any agent-initiated SFDC change via Slack
- Reactivates a paused but fully-built agent

## Implementation Notes

- Salesbot already supports: opportunity updates, contact CRUD, account updates, SOQL queries
- The `#sales-bot` channel provides natural human oversight
- Start with BD Re-engagement Monitor as the first consumer to test the pattern
- Complexity: **Medium** — requires reactivating Salesbot trigger + defining a message format for agent-to-Salesbot requests
