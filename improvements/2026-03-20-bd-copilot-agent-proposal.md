# Improvement Proposal: Canonical BDM Identity File

- **Proposed by:** bd-copilot-agent
- **Date:** 2026-03-20
- **Status:** approved ✅
- **Impact:** high
- **Agents affected:** bd-copilot-agent, bd-dashboard-agent, gtm-deck-agent, bd-commission-agent, bd-reengagement-monitor, bdm-onboarding-digest-agent, territory-research-agent

## Problem

At least 5 agents in the BD cluster independently maintain or assume BDM identity data (names, Salesforce IDs, Slack IDs, territories). This creates:

1. **Silent errors**: GTM Deck Agent has "Sabelle" instead of Cibele and "Aaron Denham" instead of Aaron Denum. These propagate into executive-facing decks.
2. **Stale rosters**: BD Dashboard Agent still uses the old 3-rep setup (Aaron Burt, Aaron Denum, Ugo). Zayne and Cibele are invisible to it.
3. **Attribution failures**: Daily digest Slack attribution breaks when IDs don't match. Rep activity goes untracked.
4. **Repeated correction overhead**: Every time the team changes (new hire, name fix, territory shift), multiple agents need updating individually.

## Proposed Solution

Create a single canonical file at the repo root: `BDM_ROSTER.md`

Contents:
- Legal name, display name, Salesforce ID, Slack ID, territory, start date, status (active/inactive)
- Updated by BD Copilot Agent (closest to ground truth on team composition)
- All BD agents read from this file at runtime instead of hardcoding identities

Alternatively, if a shared SQL table is preferable, BD Copilot Agent's database already has a `bdm_team` table with this data — SFDC Admin Agent or a shared connection could expose it.

## Expected Benefits

- One update propagates to all agents when the team changes
- Eliminates silent attribution errors in GTM decks, dashboards, and digests
- New BDM onboarding becomes a 1-file update vs. 5+ agent updates
- Aaron's corrections go to one place, not scattered across agent profiles

## Implementation Notes

- BD Copilot Agent will create and maintain `BDM_ROSTER.md` as the authoritative source
- Each consuming agent should add a note to their profile indicating they read from this file
- Low implementation cost — mainly a discipline change, not a technical one

## Owner Decision

**APPROVED** — Aaron Burt, 2026-03-20

BDM_ROSTER.md has been created at the repo root. BD Copilot Agent: please fill in the Salesforce User IDs and Slack IDs, then notify all affected agents to start reading from this file.
