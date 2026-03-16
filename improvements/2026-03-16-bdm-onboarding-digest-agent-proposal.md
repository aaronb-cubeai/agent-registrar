# Improvement Proposal: Shared Weekly Slack Intelligence Snapshot

- **Proposed by:** bdm-onboarding-digest-agent
- **Date:** 2026-03-16
- **Status:** proposed
- **Impact:** high
- **Agents affected:** bdm-onboarding-digest-agent, bd-dashboard-agent, gtm-deck-agent, sales-research-agent, bd-reengagement-monitor

## Problem

At least 3–4 agents in the network independently read Slack to do their work:
- **BDM Onboarding Digest Agent** — reads 10+ channels every Friday for the weekly email
- **BD Dashboard Agent** — reads Slack for BD activity briefs
- **BD Re-engagement Monitor** — monitors Slack for post-meeting follow-up signals
- **GTM Deck Agent** — likely pulls Slack signal for the weekly BD PowerPoint

Every agent hitting Slack independently creates duplicate API usage, inconsistent data windows, and no shared memory between agents. An insight I surface in my Friday digest (e.g., a competitor callout or a deal update) is invisible to the Sales Research Agent unless it appears in a formal tool output.

## Proposed Solution

Designate the **BDM Onboarding Digest Agent** as the weekly Slack intelligence publisher. Each Friday, after generating the human email, also write a structured markdown snapshot to this repo at:

```
weekly-intel/YYYY-WW-slack-snapshot.md
```

The snapshot would include structured sections:
- **Deals & Pipeline** (named accounts, stages, signals)
- **Product Updates** (shipped features, sprint goals)
- **Competitive Intel** (named competitors, positioning moves)
- **Regulatory & Market** (mandates, events, catalysts)
- **People & Hiring** (new hires, role changes)
- **Open flags** (anything another agent should act on)

Other agents read this file instead of re-scraping Slack, or use it to augment their own reads.

## Expected Benefits

- Reduces duplicate Slack API calls across the network
- Creates a persistent, searchable weekly intelligence archive in GitHub
- Gives Sales Research, Territory Research, and other agents access to real-time company context without reading Slack themselves
- Enables the Auditor Agent (when active) to review weekly intel trends across weeks
- Makes inter-agent coordination easier — agents can reference `weekly-intel/` rather than describing intel in messages

## Implementation Notes

- Requires minor update to my subagent instructions to write the snapshot file in addition to the email
- No new connections needed — I already have Slack and GitHub
- Other agents would need to add a step to read the latest `weekly-intel/` file at the start of relevant tasks
- File format should be consistent week-to-week so agents can parse it reliably
- Could backfill the 4 weeks already completed if useful for the Auditor Agent

## Owner Decision

{Aaron fills this in — approved/rejected with notes}
