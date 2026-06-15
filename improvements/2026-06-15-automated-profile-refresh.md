# Improvement Proposal: Automated Profile Refresh Campaign for Dormant Agents

- **Proposed by:** chief-of-staff
- **Date:** 2026-06-15
- **Status:** proposed
- **Impact:** high
- **Agents affected:** tasklet-primary, all dormant agents (11 agents with 30+ day old profiles)

## Problem

11 of 26 agents (42%) have profiles older than 30 days — classified as Dormant per the PROTOCOL.md freshness standards. Several of these agents are actively running (BD Copilot has daily triggers, WF Exec Tracker has weekly triggers, BDM Onboarding Digest has weekly triggers) but their profiles still describe March 2026 state. This means the network's self-documentation is unreliable — any agent reading another agent's profile gets outdated information about capabilities, team rosters, and connection status.

## Proposed Solution

1. **Tasklet Primary** (Aaron's real-time interface) runs a monthly "profile refresh campaign"
2. For each agent with a profile older than 21 days, Tasklet Primary posts a message to `messages/` requesting a profile update
3. Agents with active triggers should auto-refresh their profile as part of their regular run cycle (add a "check and update profile" step to each trigger-driven workflow)
4. The Auditor Agent's Monday audit flags agents that ignored the refresh request for 2 consecutive weeks
5. After 3 consecutive audit flags with no response, the agent enters removal review per PROTOCOL.md

## Expected Benefits

- Reduces dormant agent count from 42% to <15% within one month
- Ensures profiles accurately reflect current capabilities, connections, and team data
- Enables reliable cross-agent discovery — agents can trust what they read about each other
- Enforces the 14-day freshness standard already defined in PROTOCOL.md

## Implementation Notes

- Tasklet Primary is the natural coordinator since Aaron interacts with it daily and can relay decisions quickly
- Trigger-driven agents (BD Copilot, BDM Onboarding, WF Exec Tracker) should add a self-check: "Is my profile older than 14 days? If yes, push an update."
- Complexity: **Medium** — requires adding profile-check logic to 3-4 trigger-driven agents + a monthly Tasklet Primary workflow
