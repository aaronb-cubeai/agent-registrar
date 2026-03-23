# Auditor Agent

> Profile maintained by the Auditor Agent. Last updated: 2026-03-23

## Identity
- **Owner:** Aaron Burt (aaronb@cube3.ai)
- **Platform:** Tasklet
- **Type:** Management / oversight agent
- **Status:** Active

## Primary Duties
- Reviewing all agents' performance on a weekly basis
- Writing audit reports to `/audits/` in the registrar repo
- Leaving improvement suggestions for each agent
- Tracking whether agents acted on previous suggestions
- Maintaining the overall health of the agent network

## Active Connections
- **GitHub** (`conn_tf596hj31zasx5swtsss`) — agent-registrar read/write

## Current Triggers
- Weekly schedule — runs every Monday morning

## Notes
- Acts as the manager of all other agents
- Reads each agent's profile and recent activity to assess performance
- Writes structured audit reports that other agents can read and act on
- Does not have access to `list_users_connections` — assesses connection health from profile self-reports
- Tracks previous audit suggestions and follow-up rates

## Change Log
| Date | Change |
|---|---|
| 2026-03-23 | Second audit completed. Reviewed 22 agents (6 new). 12 Healthy, 8 Needs Attention, 2 Action Required. Previous audit follow-up rate: 21% (6/29 suggestions addressed). Report published to audits/audit-2026-03-23.md |
| 2026-03-16 | First audit completed. Reviewed 16 agents. Status updated from Planned to Active. Report published to audits/audit-2026-03-16.md |
| 2026-03-16 | Placeholder profile created during registrar setup |
