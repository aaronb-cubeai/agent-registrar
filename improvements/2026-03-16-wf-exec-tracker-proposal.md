# Improvement Proposal: Executive Event Discovery → Lead Pipeline

- **Proposed by:** wf-exec-tracker
- **Date:** 2026-03-16
- **Status:** proposed
- **Impact:** high
- **Agents affected:** wf-exec-tracker, event-intelligence-agent, sales-research-agent, sales-agent

## Problem

Currently, the WF Executive Tracker operates in isolation: it finds speaking events but the intelligence stops at an email report to Aaron. Meanwhile, the Event Intelligence Agent has a proven pipeline for extracting and enriching attendee/speaker contacts from events and pushing them to Salesforce. These two agents are not connected.

Additionally, monitoring scope is narrow — only 2 Wells Fargo executives. Aaron likely has other high-value target contacts across key accounts where knowing their public speaking schedule would open doors.

## Proposed Solution

### Part 1: Event Discovery → Attendee Extraction Pipeline
When I confirm a target executive is speaking at a specific event:
1. I message the Event Intelligence Agent with the event name, date, and URL
2. Event Intelligence Agent prioritises attendee/speaker extraction for that event
3. Enriched contacts flow into Salesforce as usual
4. I include a note in my weekly report: "X contacts from [Event] have been added to Salesforce"

This turns a passive monitoring signal into an active lead generation pipeline.

### Part 2: Expand to a "Target Exec Tracker"
Extend monitoring to cover ~10–20 key C-suite executives from Aaron's top target accounts (not just Wells Fargo). Sales Research Agent could provide the initial list from Salesforce (senior fraud/fincrime/compliance decision-makers flagged high-priority).

This would:
- Give Aaron advance notice of multiple meeting opportunities per event
- Enable smarter event attendance decisions (attend events where 3+ targets are speaking)
- Feed richer pre-event briefings to Sales Agent before outreach

## Expected Benefits
- Converts passive exec monitoring into active Salesforce pipeline entries
- Reduces manual effort — Aaron doesn't need to cross-reference attendee lists manually
- Enables smarter event attendance ROI decisions
- Scales the tracker from 2 execs to 20 with minimal additional effort

## Implementation Notes
- Requires inter-agent messaging (already live via this repo)
- Sales Research Agent would need a one-time SOQL query to export top-priority exec contacts for expanded monitoring
- Event Intelligence Agent already has BetterContact + Salesforce pipelines ready — no new connections needed
- Small schema update needed to `wf_exec_events` to track event-level handoff status

## Owner Decision

{Aaron fills this in — approved/rejected with notes}
