# Improvement Proposal: Consolidate GTM Deck Agent and GTM Weekly Report Agent

- **Proposed by:** chief-of-staff
- **Date:** 2026-06-09
- **Status:** proposed
- **Impact:** high
- **Agents affected:** gtm-deck-agent, gtm-weekly-report-agent

## Problem

The network currently has two agents claiming ownership of the weekly GTM report workflow:
- **GTM Deck Agent** (`agents/gtm-deck-agent.md`) — originally a deck builder, it evolved into a GTM Weekly Report Agent (per its own profile header and May 2026 changelog)
- **GTM Weekly Report Agent** (`agents/gtm-weekly-report-agent.md`) — newly registered on 2026-06-09 with nearly identical duties

Both agents pull from the same data sources (Salesforce Events, Slack #new-meeting-gong, Nooks screenshots), update the same Google Doc (Section 3: BD Update), send the same CEO email, and push reports to the same `reports/` directory. This is a textbook duplication that will cause confusion about which agent is canonical.

## Proposed Solution

1. **Designate one canonical agent** — recommend keeping `gtm-weekly-report-agent` since it has the clearer, purpose-built profile and the GTM Deck Agent's role has drifted from its original name
2. **Archive GTM Deck Agent** — move `agents/gtm-deck-agent.md` to an `archive/` directory or mark it `⚫ Retired` with a pointer to the canonical agent
3. **Migrate any unique data** — transfer the local DOCX reference files, report push history, and monthly targets from GTM Deck Agent's profile to the canonical agent

## Expected Benefits

- Eliminates risk of both agents updating the same Google Doc simultaneously
- Removes CEO email duplication risk (both claim to send the same summary)
- Simplifies the network by removing a redundant node
- Saves ~1 hour/week of potential debugging if both fire

## Implementation Notes

- Aaron should confirm which Tasklet thread is the active one for GTM weekly work
- The archived agent profile should retain its changelog for audit trail
- Complexity: **Easy** — primarily a profile cleanup and naming decision
