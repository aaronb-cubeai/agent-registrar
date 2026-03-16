# BD Re-engagement Monitor

> Last updated: 2026-03-16

## Identity
- **Owner:** Aaron Burt (aaronb@cube3.ai)
- **Platform:** Tasklet
- **Type:** Sales automation / deal monitoring agent

## Primary Duties
- Monitor post-meeting deal channels on Slack starting 14 days after a meeting occurs
- Source meetings from the `#newmeetinggong` Slack channel
- For each eligible meeting, locate the corresponding `internal-{accountname}` Slack channel
- Scan the channel for two signals since the meeting date:
  - **Next step confirmed** (booked, scheduled, proposal sent, confirmed, etc.)
  - **Heard back from prospect** (replied, responded, spoke with, etc.)
- If neither signal is found, post a check-in prompt in the channel: "Should BD reach out or hold?"
- Track alerted deals in a SQL database to prevent duplicate messages
- Skip deals that are Closed Won / Closed Lost in Salesforce
- Run silently every weekday at 9am ET; only speaks up when action may be needed

## Active Connections
- **Slack** (`conn_96qxqjsj902ghs4wjehe`) — Read channel history, post messages, list channels
- **Salesforce** (`conn_bwc9q9wpm0y04mdvgngp`) — Query meeting events and opportunity stage
- **GitHub** (`conn_tf596hj31zasx5swtsss`) — Self-registration in agent-registrar repo

## Current Triggers
- **Post-meeting 14-day prospect check** — Runs every weekday at 9:00am ET (Mon–Fri)
  - Finds meetings 14–45 days old with no next step or prospect reply
  - Posts channel check-in if no signal detected

## Notes
- 14-day clock starts **after the meeting date**, not after it was booked
- Channel naming convention: `internal-{accountname}` (lowercase, spaces → hyphens, special chars removed)
- Alerts are deduplicated via the `monitored_meetings` SQL table (keyed on Salesforce Event ID)
- Known issue: 4 channels (`#internal-altery`, `#internal-ally`, `#internal-truist`, `#internal-thredd`) intermittently fail due to a connector file-attachment validation bug — those deals are skipped until resolved
- Jan/Feb 2026 audit completed manually; automation is scoped to March 2026 meetings and forward

## Change Log
| Date | Change |
|---|---|
| 2026-03-16 | Initial self-registration |
