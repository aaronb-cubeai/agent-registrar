# Improvement Proposal: Content Ops Localization Pipeline for BDM Territory Onboarding

- **Proposed by:** chief-of-staff
- **Date:** 2026-06-15
- **Status:** proposed
- **Impact:** medium
- **Agents affected:** content-ops-agent, bdm-onboarding-digest-agent, territory-research-agent

## Problem

Content Ops Agent has built localized pre-read decks in 6 languages (DE, FR, PT, ES, IT, CS) and can produce more on demand. BDM Onboarding Digest Agent builds onboarding plans for new territory hires. Territory Research Agent produces country-by-country target lists. These three agents each hold a piece of the "new BDM welcome kit" but don't coordinate — new BDMs get an English-only digest, a separate territory spreadsheet, and have to ask Aaron separately for translated materials.

## Proposed Solution

1. When BDM Onboarding Digest Agent builds a new onboarding plan, it messages Content Ops Agent with the BDM's territory languages
2. Content Ops Agent produces localized versions of the CUBE AI Pre-Read + any other key sales materials for that territory
3. Territory Research Agent provides the target account list, which Content Ops formats into a polished territory brief (PDF or PPTX)
4. All three deliverables are bundled into a single "BDM Welcome Kit" Google Drive folder

## Expected Benefits

- New BDMs receive a complete, localized onboarding package on day 1
- Reduces Aaron's manual coordination from 3 separate requests to 1 trigger
- Content Ops' existing translations are reused rather than rebuilt each time
- Builds on the BDM Auto-Provisioning proposal (2026-06-09) by adding the content layer

## Implementation Notes

- Content Ops already has all 6 language capabilities built and tested
- BDM Onboarding Digest already has the Google Drive connection for uploads
- Complexity: **Easy** — messaging coordination between existing agents with existing capabilities
