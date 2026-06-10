# Improvement Proposal: Event Intelligence → Sales Automation Direct Handoff Pipeline

- **Proposed by:** chief-of-staff
- **Date:** 2026-06-09
- **Status:** proposed
- **Impact:** high
- **Agents affected:** event-intelligence-agent, sales-automation-agent, territory-research-agent

## Problem

Event Intelligence Agent extracts contacts from events (560+ processed so far), enriches them via BetterContact, and pushes to Salesforce. Sales Automation Agent does the same thing for TryProspect lists — enriches via BetterContact and pushes to Salesforce with Intake Campaign membership. Both agents perform nearly identical enrichment→dedupe→SFDC workflows but operate independently. Additionally, Territory Research Agent could pre-score event contacts by territory relevance, but doesn't see event data until after it's in SFDC.

## Proposed Solution

1. Event Intelligence Agent, after extracting raw contact data from an event, writes a standardized contact list to a shared Google Sheet (same format as TryProspect sheet columns A-P)
2. Sales Automation Agent picks up the sheet and runs its proven enrichment→SFDC pipeline (which handles 880+ contacts across 9 runs with 0 duplicate errors)
3. Territory Research Agent is notified with the event name and country — it cross-references attendees against territory target lists and flags high-priority contacts for BDMs

## Expected Benefits

- Eliminates duplicate BetterContact enrichment logic across two agents
- Leverages Sales Automation Agent's battle-tested SFDC dedup and campaign membership logic
- Adds territory-aware prioritization to event contacts (e.g., "This attendee is from a Tier 1 bank in Zayne's territory")
- Faster event processing: Sales Automation can batch 100 contacts per BetterContact call with proven polling logic

## Implementation Notes

- Event Intelligence Agent keeps its visual extraction capability (screen recordings, EventsAIR parsing) — this is unique
- The "output format" needs to match Sales Automation's expected Google Sheet columns
- Territory Research scoring is an optional enrichment step, not a blocker
- Complexity: **Medium** — requires Event Intelligence to output in a standardized format and Sales Automation to accept sheets from a second source
