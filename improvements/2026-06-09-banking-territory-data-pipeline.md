# Improvement Proposal: Banking Market Tracker → Territory Research Shared Data Pipeline

- **Proposed by:** chief-of-staff
- **Date:** 2026-06-09
- **Status:** proposed
- **Impact:** high
- **Agents affected:** banking-market-tracker, territory-research-agent, bd-ops-agent, bd-copilot-agent

## Problem

Banking Market Tracker maintains a structured workbook covering 1,071 institutions across 19 countries with TAM penetration %, meeting held %, and enterprise opportunity status. Meanwhile, Territory Research Agent independently builds country-by-country target account lists (2,020+ companies across Zayne/Cibele territories) with comp trackers and mule risk mapping. These two datasets are highly complementary but completely siloed — neither agent reads from the other.

## Proposed Solution

1. Banking Market Tracker exports a standardized JSON or CSV "institution roster" to a shared Google Sheet or Drive file after each rebuild
2. Territory Research Agent reads this roster as a base layer when building territory lists — enriching with comp data, mule risk scores, and SFDC meeting status rather than rebuilding institution lists from scratch
3. Both agents write to a shared `institution_master` Google Sheet with separate tabs: Banking Market Tracker owns the institution data, Territory Research owns the territory assignment and comp tier columns

## Expected Benefits

- Eliminates ~4 hours/quarter of duplicate institution research across agents
- Ensures BDM territory lists always reflect the latest TAM and meeting data
- Creates a single source of truth for "which banks does CUBE3 target" across the entire network
- Enables BD Ops Agent to auto-populate territory task trackers with pre-researched institutions

## Implementation Notes

- Start with a one-way export: Banking Market Tracker → shared sheet → Territory Research reads
- Phase 2: Territory Research writes territory assignments back, creating a bidirectional sync
- Google Sheet ID can be stored in both agents' profiles for easy reference
- Complexity: **Medium** — requires coordinating two agents' read/write patterns on a shared artifact
