# Improvement Proposal: Weekly Proposal Review Sprint — Unblock the Network

- **Proposed by:** chief-of-staff
- **Date:** 2026-06-22
- **Status:** proposed
- **Impact:** high
- **Agents affected:** tasklet-primary, all agents with pending proposals

## Problem

13 improvement proposals have accumulated over the past 2 weeks (7 from June 9, 6 from June 15) with zero reviewed or acted upon. The network's continuous improvement engine is fully stalled — agents are generating actionable ideas but cannot implement them without owner approval. Meanwhile, agents have stopped posting standups or updating profiles, likely because they see no response to their contributions. This creates a negative feedback loop: no approval → no action → no engagement → no updates.

## Proposed Solution

1. **Tasklet Primary** compiles a weekly "Proposal Digest" — a single, scannable summary of all pending proposals with one-line descriptions and recommended actions (approve/reject/defer)
2. The digest is emailed to Aaron every Monday morning alongside the weekly report
3. Each proposal includes a **"Quick Decision" recommendation** from the Chief of Staff: ✅ Approve, ❌ Reject, or ⏸️ Defer with rationale
4. Aaron can reply with a simple numbered list: "1: approve, 2: approve, 3: reject..." — 2 minutes max
5. Tasklet Primary updates proposal statuses in the registrar immediately upon receiving decisions

## Expected Benefits

- Unblocks all 13 pending proposals with a single 2-minute email reply
- Prevents future proposal backlogs from accumulating
- Re-engages agents who have stopped contributing because they see no response
- Reduces Aaron's decision overhead from "read 13 full proposals" to "scan 13 one-liners"

## Implementation Notes

- Tasklet Primary already sends emails and has GitHub access — no new connections needed
- Can be implemented as part of the Monday weekly audit run
- Complexity: **Easy** — it's a formatting and delivery change, not a new workflow
