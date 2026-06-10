# Improvement Proposal: Define Clear Swim Lanes for Auditor Agent vs. Improvement Agent

- **Proposed by:** chief-of-staff
- **Date:** 2026-06-09
- **Status:** proposed
- **Impact:** medium
- **Agents affected:** auditor-agent, improvement-agent

## Problem

Both the Auditor Agent and Improvement Agent perform weekly audits of the agent network and file improvement proposals. Their profiles describe overlapping scopes:
- Auditor Agent: "Reviews all agents' performance weekly, writes audit reports, leaves improvement suggestions"
- Improvement Agent: "Audits the entire agent network weekly, identifies inefficiencies, files concrete actionable proposals"

Without clear boundaries, both agents will produce redundant audit reports covering the same ground, and it's unclear which one Aaron should prioritize.

## Proposed Solution

Define distinct responsibilities:

**Auditor Agent (Monday)** — focuses on **compliance and health**:
- Profile freshness checks (stale/dormant detection)
- Suggestion follow-up tracking (did agents act on past feedback?)
- Connection health verification
- Trigger status audits
- Output: structured audit report with health scores (Healthy / Needs Attention / Action Required)

**Improvement Agent (Friday)** — focuses on **innovation and cross-agent optimization**:
- New workflow ideas and cross-agent data connections
- Efficiency proposals (deduplication, automation gaps)
- Missing agent identification
- Stale proposal tracking and escalation
- Output: prioritized improvement proposals with complexity ratings

## Expected Benefits

- Zero overlap between audit reports and improvement proposals
- Aaron gets health checks on Monday and fresh ideas on Friday — complementary cadence
- Both agents can reference each other's outputs: Improvement Agent can cite Auditor findings, Auditor can verify if Improvement proposals were implemented
- Clearer accountability: health issues → Auditor; optimization ideas → Improvement Agent

## Implementation Notes

- Update both agent profiles to reference these swim lanes explicitly
- Auditor Agent should stop filing improvement proposals; only flag health issues
- Improvement Agent should stop tracking profile freshness; only propose new workflows
- Complexity: **Easy** — profile updates and instruction changes only, no new infrastructure
