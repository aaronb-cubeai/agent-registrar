# Improvement Proposal: Unified BDM Roster — Single Source of Truth

- **Proposed by:** chief-of-staff
- **Date:** 2026-06-15
- **Status:** proposed
- **Impact:** high
- **Agents affected:** bd-dashboard-agent, bd-copilot-agent, gtm-weekly-report-agent, bd-commission-agent, sales-dashboard-agent, territory-research-agent

## Problem

At least 6 agents maintain their own copy of the BDM team roster — names, territories, Salesforce IDs, and Slack usernames. BD Dashboard Agent already flagged this: "Always read from BDM_ROSTER.md — do not hardcode names here." But BD Copilot hardcodes a full roster table, GTM Deck Agent lists "Zayne, Ugo, Cibele" with different spellings, BD Commission Agent maintains its own BDM_Owner__c picklist, and Territory Research maps territories independently. When a rep joins or leaves, each agent must be updated individually — and several are 87+ days stale, still referencing March 2026 team state.

## Proposed Solution

1. Create a single `BDM_ROSTER.md` file in the root of the agent-registrar repo
2. Include: Name, Territory (countries), Salesforce User ID, Slack Username, Start Date, Status (active/departed)
3. All agents that reference BDM data MUST read from this file at runtime rather than hardcoding
4. When a rep joins or departs, update ONE file — all agents automatically pick up the change
5. BD Dashboard Agent (already the most diligent about this) maintains the file as the canonical owner

## Expected Benefits

- Eliminates roster drift across 6+ agents (currently 3 agents show different rep counts)
- Reduces BDM onboarding work from "update 6 agents" to "update 1 file"
- Prevents bugs like the BD Dashboard filter gap (only 3 of 5 reps in filters)
- Single-file audit trail for team changes

## Implementation Notes

- BD Dashboard Agent already references a local BDM_ROSTER.md — promote this to the repo root
- Add a changelog section to the roster file
- Complexity: **Easy** — one new file + profile updates to reference it
