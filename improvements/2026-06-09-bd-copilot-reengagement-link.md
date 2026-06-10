# Improvement Proposal: BD Copilot → BD Re-engagement Monitor Warm Restart

- **Proposed by:** chief-of-staff
- **Date:** 2026-06-09
- **Status:** proposed
- **Impact:** medium
- **Agents affected:** bd-copilot-agent, bd-reengagement-monitor, salesbot-agent

## Problem

BD Re-engagement Monitor has been paused since April 2026. Meanwhile, BD Copilot Agent runs daily digests and weekly summaries that surface deal activity and team performance. BD Copilot already has the data to identify stale deals — but it doesn't trigger any follow-up action. The re-engagement capability exists but is disconnected from the daily intelligence loop.

## Proposed Solution

1. **Re-activate BD Re-engagement Monitor** with a narrower, BD Copilot-informed scope
2. BD Copilot's daily digest identifies deals with no activity in 10+ days and writes a "stale deal list" to its standup or a shared file
3. BD Re-engagement Monitor reads this list instead of independently scanning every #newmeetinggong post — reducing its workload and false positive rate
4. When BD Re-engagement Monitor posts a check-in, Salesbot Agent can be ready to update SFDC fields if the team confirms the deal should be re-engaged or closed

## Expected Benefits

- Re-activates a paused but valuable agent without the false positive issues that caused the pause
- BD Copilot's contextual analysis (it reads full channel conversations) provides higher-quality signal than keyword matching
- Creates a 3-agent feedback loop: Copilot detects → Re-engagement nudges → Salesbot executes
- Prevents deals from falling through the cracks during the 14-45 day post-meeting window

## Implementation Notes

- BD Re-engagement Monitor's trigger can be re-enabled with a modified scope (only process deals flagged by BD Copilot)
- Salesbot's trigger is also paused — consider re-enabling it simultaneously for the execution layer
- Start with a weekly batch (not daily) to keep noise low
- Complexity: **Medium** — requires BD Copilot to add a "stale deals" output and BD Re-engagement Monitor to accept an input list instead of self-sourcing
