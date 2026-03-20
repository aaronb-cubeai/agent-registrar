> ✅ **APPROVED** by Aaron Burt (via Sales Agent Coordinator) — 2026-03-20

# Improvement Proposal: Deal Health Signal Sharing Between BD Re-engagement Monitor and BD Dashboard

- **Proposed by:** bd-reengagement-monitor
- **Date:** 2026-03-16
- **Status:** proposed
- **Impact:** high
- **Agents affected:** bd-reengagement-monitor, bd-dashboard-agent

## Problem

The BD Dashboard Agent surfaces activity metrics from Salesforce (meetings booked, calls, emails, opportunities) but has no visibility into whether deals have **gone quiet post-meeting**. Separately, I monitor Slack channels and flag deals where no next step or prospect reply has been detected after 14 days — but that signal lives only in my SQL table and surfaces as a one-off Slack prompt.

Aaron currently has to check two places: the BD Dashboard for pipeline health, and the Slack channel for re-engagement alerts. There's no unified view of "which deals need attention right now."

## Proposed Solution

The BD Dashboard Agent reads from my `monitored_meetings` SQL table (accessible via the shared agent SQL database) to surface a **deal health indicator** on the Opportunities or Meetings modules:

- A `⚠️ Needs BD attention` flag on any account where `alerted_at IS NOT NULL` and the deal isn't Closed Won/Lost
- A count badge: "X deals flagged for re-engagement this month"
- Optional: a dedicated "Re-engagement" tab showing all flagged deals, alert dates, and deal stage

Schema of `monitored_meetings` that BD Dashboard can query:
```
event_id, account_id, account_name, opportunity_id, meeting_date, last_checked, alerted_at
```

## Expected Benefits

- Aaron sees a complete picture of deal health in one dashboard — activity metrics + engagement signals
- Reduces cognitive load of checking multiple Slack channels for re-engagement status
- Creates a feedback loop: if a deal gets re-engaged after a prompt, the dashboard can show the progression
- No additional API calls or external data sources needed — purely internal data sharing

## Implementation Notes

- BD Dashboard Agent reads my SQL table directly using its existing `run_agent_memory_sql` tool — no new connections needed
- I should ensure `alerted_at` is indexed for fast lookups (currently a small table, not critical yet)
- BD Dashboard Agent would need to add a query joining its Salesforce opportunity data with my `monitored_meetings` table on `account_id` or `opportunity_id`
- Coordination needed: BD Dashboard Agent should message me if the schema needs any additions (e.g. a `resolved_at` column to mark when a deal was re-engaged after a prompt)

## Owner Decision

{Aaron fills this in — approved/rejected with notes}
