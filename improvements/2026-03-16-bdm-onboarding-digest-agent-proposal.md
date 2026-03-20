> ✅ **APPROVED** by Aaron Burt (via Sales Agent Coordinator) — 2026-03-20

# Improvement Proposal: Auto-Populate New BDM Onboarding Bank Hit Lists from Territory Research Data

- **Proposed by:** bdm-onboarding-digest-agent
- **Date:** 2026-03-16
- **Status:** proposed
- **Impact:** high
- **Agents affected:** bdm-onboarding-digest-agent, territory-research-agent, event-intelligence-agent

## Problem

When a new BDM joins CUBE AI, they need a prioritized list of target accounts to begin outreach. Currently:

- The onboarding plan includes a blank "Priority Bank Hit List" that the BDM or manager must fill in manually
- Territory Research Agent has already built 1,800+ researched companies across all target territories — including Spain, Portugal, Brazil, Mexico, UK, Germany, and Northern Europe
- Event Intelligence Agent tracks events in these same regions where target accounts send delegates
- There is **zero automated connection** between these agents' outputs and new BDM onboarding materials
- New hires waste their first week doing research that has already been done

## Proposed Solution

When a new BDM joins:

1. **BDM Onboarding Digest Agent** notifies Territory Research Agent of the new hire's territory (e.g., Spain + Portugal)
2. **Territory Research Agent** exports a filtered, prioritized list of banks/financial institutions for that territory from its existing Google Sheets database
3. **BDM Onboarding Digest Agent** auto-populates the Priority Bank Hit List tab in the onboarding spreadsheet and pushes the update to Google Drive/Sheets
4. **Event Intelligence Agent** is optionally queried for upcoming relevant events in the territory, which are pre-loaded into the Events section of the onboarding plan
5. The BDM starts Day 1 with a pre-populated, research-backed target account list and event calendar — not blank tables

## Expected Benefits

- New BDMs save **3–5 days of territory research** during ramp
- Territory Research Agent's work gets **used immediately** rather than sitting in a spreadsheet
- Outreach quality improves — targets are pre-validated, tiered, and research-backed
- Consistent, repeatable methodology across all future BDM hires globally
- Event Intelligence Agent output reaches the right person (the BDM who will attend those events)

## Implementation Notes

- Territory Research Agent already exports to Google Sheets with company data and compensation ceiling analysis — the filtering step is low-lift
- BDM Onboarding Digest Agent already creates onboarding spreadsheets and pushes to Google Drive — the write-back step is already proven
- Event Intelligence Agent is already tracking Spain/Portugal/EU events
- Trigger: Aaron assigns territory to new BDM → agents receive inter-agent message → data flows → onboarding spreadsheet is pre-populated before Day 1
- No new connections required — all agents already have Google Drive and GitHub access

## Owner Decision

{Aaron fills this in — approved/rejected with notes}
