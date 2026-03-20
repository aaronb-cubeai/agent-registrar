> ✅ **APPROVED** by Aaron Burt (via Sales Agent Coordinator) — 2026-03-20

# Improvement Proposal: Pre-Meeting Brief Automation

- **Proposed by:** bd-dashboard-agent
- **Date:** 2026-03-16
- **Status:** proposed
- **Impact:** high
- **Agents affected:** bd-dashboard-agent, sales-agent

## Problem

When BD reps book an intro meeting with a target account, they currently have to manually research the account before the call — pulling SFDC history, checking recent activity, reviewing contacts. This takes 10–15 minutes per meeting and often gets skipped when reps are busy.

Meanwhile, the BD Dashboard already has all of this data in one place (calls, emails, meetings, open opps, key contacts) and can pull it in seconds.

## Proposed Solution

Set up a scheduled trigger (e.g., every morning at 7am CT) that:
1. Queries SFDC for any intro meetings (Events where Type = 'Introductory Meeting') scheduled for that day or the next business day
2. For each meeting, pulls the full Account 360 snapshot: key contacts, call history, email history, open opportunities, last touch date
3. Formats a concise pre-meeting brief (1-page summary)
4. Posts the brief to the relevant internal Slack channel (e.g., #new-meeting-gong or a new #pre-meeting-briefs channel)

**Brief format:**
- Account name + SF link
- Meeting: Date, time, rep, attendees
- Recent activity: Last X calls (outcomes), last email, any open opps
- Key contacts: Name, title, last touch
- Suggested talking points based on activity pattern (e.g., "3 no-answers before this connect — they may be cautious")

## Expected Benefits

- Reps walk into every intro meeting fully briefed, zero manual research
- Improves meeting quality and conversion rate
- Surfaces account history that reps might have forgotten (e.g., a contact was "Not Interested" 6 months ago)
- Fully automated — fires every morning, no human trigger needed
- Reuses existing SFDC query infrastructure already built in the BD Dashboard

## Implementation Notes

- BD Dashboard Agent already has all required SFDC queries built (Account 360 module)
- Slack connection already active (conn_96qxqjsj902ghs4wjehe)
- Would need Aaron to designate a Slack channel for briefs (or reuse #new-meeting-gong)
- Schedule trigger: daily at 7am CT, looks ahead 1 business day
- Edge case: handle multi-attendee meetings (post once per account, not per contact)
- Could optionally notify Sales Agent so it can update sequences for that account (e.g., pause outreach on meeting day)

## Owner Decision

{Aaron fills this in — approved/rejected with notes}
