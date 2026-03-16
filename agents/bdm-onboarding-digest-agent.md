# BDM Onboarding Digest Agent

> Last updated: 2026-03-16

## Identity
- **Owner:** Aaron Burt (aaronb@cube3.ai)
- **Platform:** Tasklet
- **Type:** Slack digest & onboarding automation agent

## Primary Duties
- Scans key CUBE AI Slack channels every Friday and synthesizes the week's key learnings into a ~2-page briefing
- Emails the digest to Aaron in a forward-ready format so he can send it to new EU BDMs (Cibele & Zayne) joining in March 2026
- Covers: product updates, sales & BD activity, competitive intelligence, customer news, marketing & events, and cultural/team observations
- Runs automatically every Friday at 8:00 AM CT via a scheduled trigger
- Channels monitored: sales-bd, product-updates, competition, customer-success, marketing, events, general, team announcements, and other active channels

## Active Connections
- **Slack** (`conn_96qxqjsj902ghs4wjehe`) — list channels, get conversation history, search messages
- **GitHub** (`conn_tf596hj31zasx5swtsss`) — agent registrar read/write

## Current Triggers
- **Weekly BDM Slack Digest Email** — Every Friday at 8:00 AM CT (`0 8 * * 5`, America/Chicago)
  - Trigger ID: `cti_vy66dqs4e2hye6jakakq`

## Notes
- Digest is written in Aaron's voice, formatted so it can be forwarded directly to new hires without editing
- Covers the prior Mon–Fri work week
- Uses a subagent (`/agent/subagents/weekly-bdm-digest.md`) to handle Slack fetching and digest generation, keeping context lean
- Prioritises signal over noise: named deals, named people, product specifics, competitor callouts, and regulatory catalysts
- First digest sent: week of Feb 18–24, 2026

## Change Log
| Date | Change |
|---|---|
| 2026-03-16 | Initial self-registration |
