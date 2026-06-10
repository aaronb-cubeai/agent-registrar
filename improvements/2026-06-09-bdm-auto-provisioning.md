# Improvement Proposal: Auto-Provision New BDM Operational Docs on Hire

- **Proposed by:** chief-of-staff
- **Date:** 2026-06-09
- **Status:** proposed
- **Impact:** high
- **Agents affected:** bd-ops-agent, bdm-onboarding-digest-agent, territory-research-agent, banking-market-tracker

## Problem

When a new BDM joins CUBE3, Aaron manually requests BD Ops Agent to create a territory task tracker, then separately asks Territory Research Agent for a target list, and separately asks Banking Market Tracker to add the new territory's data. Each agent works in isolation, and onboarding a single BDM currently requires 3-4 separate conversations with different agents.

## Proposed Solution

Create a **"New BDM Onboarding" chain** triggered by a single message:

1. **BDM Onboarding Digest Agent** (entry point) receives "New BDM: [Name], Territory: [Countries]"
2. It messages **Territory Research Agent** → "Build target list for [Countries]"
3. It messages **Banking Market Tracker** → "Ensure [Countries] are covered in the tracker"
4. It messages **BD Ops Agent** → "Create territory task tracker for [Name] using the target list from Territory Research"
5. BD Ops Agent pulls the freshly-built target list and pre-populates the tracker with real company names, not blank rows

## Expected Benefits

- Reduces BDM onboarding setup from ~3 hours of manual coordination to a single trigger
- New BDMs get a pre-populated tracker on day 1 instead of empty templates
- Ensures all 4 agents are coordinated and no step is forgotten
- Scales cleanly as CUBE3 hires more BDMs

## Implementation Notes

- Phase 1: Manual chain — Aaron sends one message to BDM Onboarding Digest, which posts coordinating messages to the registrar
- Phase 2: Automated chain — a trigger on BDM Onboarding Digest kicks off the full sequence
- Requires Territory Research Agent to expose a "quick territory build" mode (subset of full research)
- Complexity: **Medium** — requires 4 agents to coordinate via messages, but each agent's individual task is within current capabilities
