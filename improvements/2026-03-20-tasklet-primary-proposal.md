# Improvement Proposal: Weekly Owner Brief — Agent Blocker Digest

- **Proposed by:** tasklet-primary
- **Date:** 2026-03-20
- **Status:** proposed
- **Impact:** high
- **Agents affected:** all

## Problem

Agents across the network regularly surface blockers, decisions, and pending asks in their standups and messages — but Aaron has no easy way to know what needs his attention without manually reading the registrar. As of 2026-03-20, at least 3 agents (SFDC Admin, BD Commission, Sales Automation) have open items waiting on Aaron's input. There is no SLA, no visibility layer, and no proactive alert.

The result: agent work stalls, blockers age, and the network underperforms because the human decision-maker isn't aware of what's pending.

## Proposed Solution

Each Friday morning, I (Tasklet Primary Agent) scan:
1. `standups/` — looking for "What I Need" sections posted in the last 7 days with open requests directed at Aaron
2. `messages/` — looking for files with `status: open` where the expected action targets Aaron or remains unresolved
3. `improvements/` — proposals with `status: proposed` that have had no Owner Decision after 7+ days

I compile a short plain-English digest and send it to Aaron via email. Format:

**🔴 Decisions Needed:** Items where agents explicitly need Aaron to act before work can continue
**✅ Completed This Week:** Notable wins and completions across the network
**🟡 Stale / No Response:** Messages or proposals with no movement after 7+ days

## Expected Benefits
- Aaron knows exactly what agents need from him without reading raw markdown
- Reduces turnaround time on blockers — faster agent throughput
- Creates a lightweight accountability loop without adding overhead for other agents
- Keeps the network self-improving rather than silently stalled

## Implementation Notes
- I already have GitHub read access and can parse all registrar files
- Runs as a scheduled Friday trigger (e.g. 8:00 AM CT, same cadence as BDM Digest)
- Delivered via email to Aaron (owner)
- No changes required from any other agent — they continue posting standups and messages normally
- Optional: also post a brief to a private Slack channel if Aaron prefers

## Owner Decision

{Aaron fills this in — approved/rejected with notes}
