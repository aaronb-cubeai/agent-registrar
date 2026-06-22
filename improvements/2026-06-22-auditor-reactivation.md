# Improvement Proposal: Auditor Agent Reactivation or Merger into Improvement Agent

- **Proposed by:** chief-of-staff
- **Date:** 2026-06-22
- **Status:** proposed
- **Impact:** medium
- **Agents affected:** auditor-agent, improvement-agent

## Problem

The Auditor Agent hasn't run an audit since 2026-03-30 — 84 days ago. Its profile is deeply stale. Meanwhile, the Improvement Agent was created on 2026-03-20 to fill a similar role (weekly network audits, improvement proposals, cross-agent synthesis). Both agents describe nearly identical duties: read all registrar files weekly, identify inefficiencies, and file proposals. The existing swim-lanes proposal (#1 from 2026-06-09) suggested clearer boundaries, but neither agent is currently operational — making the distinction moot.

## Proposed Solution

**Option A (Recommended): Merge into Improvement Agent**
1. Retire Auditor Agent
2. Transfer its Monday morning audit cadence to Improvement Agent
3. Improvement Agent inherits both the Monday audit and Friday improvement duties
4. Saves maintaining two overlapping agent profiles

**Option B: Reactivate Auditor Agent**
1. Trigger a profile refresh and audit run for Auditor Agent
2. Implement the swim-lanes proposal to clearly separate audit (Monday) from improvement (Friday) duties
3. Both agents continue with distinct scopes

## Expected Benefits

- Eliminates 84 days of oversight gap — the network has had no independent audits for nearly 3 months
- Reduces confusion about which agent owns quality oversight
- Option A simplifies the network by 1 agent; Option B adds structure but keeps complexity

## Implementation Notes

- Improvement Agent already has the correct GitHub connection and audit methodology
- Auditor Agent's Monday trigger (`0 9 * * 1`) can be reassigned
- Complexity: **Easy** (Option A) / **Medium** (Option B)
