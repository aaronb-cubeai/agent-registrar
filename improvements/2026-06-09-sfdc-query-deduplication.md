# Improvement Proposal: Salesforce Query Result Sharing via Cached Snapshots

- **Proposed by:** chief-of-staff
- **Date:** 2026-06-09
- **Status:** proposed
- **Impact:** medium
- **Agents affected:** bd-dashboard-agent, sales-dashboard-agent, gtm-weekly-report-agent, bd-copilot-agent, bd-commission-agent, salesbot-agent

## Problem

At least 6 agents independently query Salesforce for overlapping data: meetings (Events), opportunities, pipeline stages, and rep activity. Each agent runs its own SOQL queries, often for the same time ranges and the same rep roster. This creates:
- Unnecessary Salesforce API usage (risk of rate limiting)
- Potential metric discrepancies when agents use slightly different filters or definitions
- Redundant processing of the same underlying data

Sales Dashboard Agent already flagged this: "Metric definitions should align with the GTM Weekly Report Agent and BD Dashboard Agent."

## Proposed Solution

1. **Designate BD Dashboard Agent as the canonical SFDC metrics provider** — it already has the most complete query set and direct API access
2. BD Dashboard Agent publishes a **weekly SFDC snapshot** to a shared Google Sheet with standardized tabs: Events (meetings), Opportunities (pipeline), Tasks (calls/emails), Account Activity
3. Other agents read from this snapshot for their reporting needs instead of running independent queries
4. Agents that need real-time data (e.g., Salesbot for on-demand lookups) continue querying directly but use the snapshot's metric definitions as the canonical reference

## Expected Benefits

- Eliminates metric discrepancies across 6 reporting surfaces
- Reduces Salesforce API calls by ~60% across the network
- Creates a single source of truth for "how many meetings did BD hold this week"
- Makes debugging number mismatches trivial — check the snapshot

## Implementation Notes

- Snapshot should be time-stamped and versioned so agents know data freshness
- Start with a weekly cadence matching the GTM Weekly Report cycle
- BD Dashboard Agent already has all required connections (Salesforce, Google Drive, GitHub)
- Complexity: **Medium** — BD Dashboard Agent needs a new "publish snapshot" workflow; consumers need to switch from direct queries to reading the sheet
