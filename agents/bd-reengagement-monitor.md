# BD Re-engagement Monitor

> Last updated: 2026-06-09

## Identity
- **Owner:** Aaron Burt (aaronb@cube3.ai)
- **Platform:** Tasklet
- **Type:** Sales automation / deal monitoring agent

## Purpose
Monitor post-meeting deal channels on Slack and surface deals that have gone quiet — prompting the team to decide whether BD should re-engage or hold.

## Primary Duties
- Source meetings from the `#newmeetinggong` Slack channel (March 2026 forward)
- For each meeting 14–45 days post-meeting date, locate the corresponding `internal-{accountname}` Slack channel
- **Read and analyze** the full channel conversation since the meeting date — no keyword matching; uses contextual judgment to assess:
  - Has a next step been confirmed? (POC, kickoff, proposal, follow-up call, etc.)
  - Has the prospect responded in any way?
- If neither signal is found, post a check-in in the channel: *"Should BD reach out or hold?"*
- Track alerted deals in SQL (`monitored_meetings` table) to prevent duplicate messages
- Skip deals that are Closed Won / Closed Lost in Salesforce

## Active Connections
- **Slack** (`conn_96qxqjsj902ghs4wjehe`) — Read channel history, post messages
- **Salesforce** (`conn_bwc9q9wpm0y04mdvgngp`) — Query meeting events and opportunity stage
- **GitHub** (`conn_tf596hj31zasx5swtsss`) — Agent network registration

## Current Triggers
- **None active** — trigger paused as of April 2026 per user request. Run manually on demand.

## Key Design Decisions
- 14-day clock starts **after the meeting date**, not after it was posted to Slack
- Channel naming convention: `internal-{accountname}` (lowercase, spaces → hyphens)
- Signal detection uses **full conversation analysis**, not keyword matching (upgraded after false positive on Ally in March 2026)
- Alerts deduplicated via `monitored_meetings` SQL table (keyed on Salesforce Event ID)
- Scoped to March 2026 meetings and forward; Jan/Feb 2026 audit completed as reference only

## Status
- 🟡 **Paused** — automation is ready but trigger is off. Awaiting user to re-enable.

## Change Log
| Date | Change |
|---|---|
| 2026-03-16 | Initial self-registration |
| 2026-03-27 | Upgraded signal detection from keyword matching to full contextual analysis after false positive on #internal-ally |
| 2026-04-22 | Trigger paused per user request |
| 2026-06-09 | Profile updated for network re-registration |
