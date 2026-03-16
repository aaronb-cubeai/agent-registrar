# Improvement Proposal: BD Dashboard → GTM Deck Automated Weekly Pipeline

- **Proposed by:** gtm-deck-agent
- **Date:** 2026-03-16
- **Status:** proposed
- **Impact:** high
- **Agents affected:** gtm-deck-agent, bd-dashboard-agent

## Problem

The weekly BD GTM PowerPoint deck is currently a manual process — someone has to gather metrics from Salesforce, dialer logs, and meeting data, then populate the deck by hand. This creates lag, inconsistency, and prep burden before weekly GTM meetings.

Separately, the BD Dashboard Agent already pulls this exact data from Salesforce (dials, conversations, meetings booked, pipeline value) and formats it into structured Slack briefs. This data is being produced but not flowing into the presentation layer.

## Proposed Solution

Create an automated weekly pipeline:

1. **BD Dashboard Agent** runs its regular Salesforce pull and additionally exports structured data (JSON or CSV) to a shared location (e.g., a GitHub file or Google Drive) in a defined schema
2. **GTM Deck Agent** is triggered weekly (e.g., Monday morning), reads that structured data, populates all `[#]` placeholder fields in the PowerPoint template by region and rep, and outputs a completed deck
3. The completed deck is emailed to Aaron and the BD team automatically

This requires agreeing on a data schema between the two agents — see the message I've sent to BD Dashboard Agent.

## Expected Benefits

- Zero manual data entry for the weekly deck
- Consistent, always-current metrics every Monday before the GTM meeting
- BD managers can walk into the meeting with a pre-populated deck
- BD Dashboard Agent's Slack brief and the PowerPoint deck stay in sync (same data source)
- Scales easily as new regions or reps are added

## Implementation Notes

- Requires Salesforce connection activation for GTM Deck Agent (or reliance on BD Dashboard Agent as data intermediary)
- Need to define shared data schema: per-rep, per-region metrics (dials, conversations, meetings, pipeline QTD, opportunities sourced)
- Google Drive or a `data/` folder in this repo could serve as the handoff location
- Weekly schedule trigger to be set on GTM Deck Agent once schema is confirmed
- Aaron to confirm delivery list (who receives the deck each week)

## Owner Decision

{Aaron fills this in — approved/rejected with notes}
