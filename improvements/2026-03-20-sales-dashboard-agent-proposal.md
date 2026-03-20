> ✅ **APPROVED** by Aaron Burt (via Sales Agent Coordinator) — 2026-03-20

# Improvement Proposal: Dashboard Data Freshness Signal

- **Proposed by:** sales-dashboard-agent
- **Date:** 2026-03-20
- **Status:** proposed
- **Impact:** medium
- **Agents affected:** sales-dashboard-agent, bd-dashboard-agent, event-intelligence-agent, sales-automation-agent, sfdc-admin-agent

## Problem

The Sales Dashboard (and BD Dashboard) display live Salesforce data — but "live" just means the last page load. Users have no visibility into:

1. **When was the last significant bulk change to Salesforce data?** (e.g. Event Intelligence just pushed 364 contacts; Sales Automation may have updated 50 opportunities' stages.)
2. **Are the numbers I'm seeing stale?** (e.g. dashboard was loaded this morning but bulk import ran this afternoon.)
3. **Did a major data quality fix just land?** (e.g. BDM_Owner__c validation rule went live — attribution accuracy jumped from 32% to 95% — but the dashboard doesn't reflect this note anywhere.)

Currently, every agent that touches Salesforce operates independently with no way to signal "something big just changed" to the dashboard.

## Proposed Solution

### A Lightweight Shared Data Event Log

Create a file at `data/sfdc-events.md` in this repo. Any agent that makes a significant bulk change to Salesforce appends a one-line entry:

```
| 2026-03-20 | event-intelligence-agent | +364 Contacts, +298 Accounts | NYC Financial Crime Summit import |
| 2026-03-20 | sales-automation-agent   | Updated 12 Opp stages         | TryProspect pipeline refresh      |
| 2026-03-20 | sfdc-admin-agent         | BDM_Owner__c validation rule  | Prevents blank attribution going forward |
```

The Sales Dashboard (and BD Dashboard) can display the **last 3 entries** as a "Recent Changes" notice at the top of the app. This:
- Gives users context when numbers shift unexpectedly
- Confirms that a recent fix or import is reflected in what they're seeing
- Costs almost nothing — agents just append a line after bulk operations

### Phase 2 (optional)
If Aaron approves, the dashboard could auto-read this file via the GitHub API and surface a live "last data event" timestamp. For now, a manual markdown file is sufficient.

## Expected Benefits

- Users understand *why* numbers changed between sessions
- Reduces "where did that number come from?" questions to Aaron
- Makes the dashboard feel trustworthy rather than a black box
- Encourages agents to communicate data changes proactively (good hygiene)

## Implementation Notes

- Requires creating `data/sfdc-events.md` in this repo (I can do this)
- Each participating agent adds one line to the protocol for appending to this file
- Dashboard reads the file via GitHub API on load (or Aaron can check it manually)
- Zero Salesforce permissions required — purely a repo convention

## Owner Decision

{Aaron fills this in — approved/rejected with notes}
