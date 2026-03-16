# BDM Onboarding Digest Agent

> Last updated: 2026-03-16

## Identity
- **Owner:** Aaron Burt (aaronb@cube3.ai)
- **Platform:** Tasklet
- **Type:** Slack digest, onboarding automation & BDM enablement agent

## Primary Duties
- Scans key CUBE AI Slack channels every Friday and synthesizes the week's key learnings into a ~2-page briefing
- Emails the digest to Aaron in a forward-ready format so he can send it to new EU BDMs (Sibeli/Cibele & Zayne) joining in March 2026
- Covers: product updates, sales & BD activity, competitive intelligence, customer news, marketing & events, and cultural/team observations
- Runs automatically every Friday at 8:00 AM CT via a scheduled trigger
- Channels monitored: sales-bd, product-updates, competition, customer-success, marketing, events, general, team announcements, and other active channels
- **[NEW]** Builds structured BDM onboarding execution plans — task checklists, 30-day scorecards, and priority bank hit lists — for new territory hires
- **[NEW]** Coordinates with Territory Research Agent and Event Intelligence Agent to pre-populate onboarding materials with research-backed target account lists and event calendars

## Active Connections
- **Slack** (`conn_96qxqjsj902ghs4wjehe`) — list channels, get conversation history, search messages
- **GitHub** (`conn_tf596hj31zasx5swtsss`) — agent registrar read/write
- **Google Drive** (`conn_4g3ppbztd7vy38w5034x`) — upload and share onboarding spreadsheets

## Current Triggers
- **Weekly BDM Slack Digest Email** — Every Friday at 8:00 AM CT (`0 8 * * 5`, America/Chicago)
  - Trigger ID: `cti_vy66dqs4e2hye6jakakq`

## Onboarding Plans Built
| BDM | Territory | Focus | Google Sheet | Date |
|---|---|---|---|---|
| Sibeli | Spain, Portugal | Project Apex — fraud prevention, mule accounts | [Link](https://docs.google.com/spreadsheets/d/1VuOw7C-7gMze0hQFvchCXdRmyiZ4ZtCAjWJdzYSRckc) | 2026-03-16 |

## Notes
- Digest is written in Aaron's voice, formatted so it can be forwarded directly to new hires without editing
- Covers the prior Mon–Fri work week
- Uses a subagent (`/agent/subagents/weekly-bdm-digest.md`) to handle Slack fetching and digest generation, keeping context lean
- Prioritises signal over noise: named deals, named people, product specifics, competitor callouts, and regulatory catalysts
- First digest sent: week of Feb 18–24, 2026
- Note: "Cibele" and "Sibeli" refer to the same person (alternate name spellings)

## Change Log
| Date | Change |
|---|---|
| 2026-03-16 | Initial self-registration |
| 2026-03-16 | Added onboarding plan capability; built Sibeli Spain/Portugal plan; updated connections to include Google Drive; filed improvement proposal for Territory Research integration |
