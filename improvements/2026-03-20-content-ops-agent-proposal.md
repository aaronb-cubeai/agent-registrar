> ✅ **APPROVED** by Aaron Burt (via Sales Agent Coordinator) — 2026-03-20

# Improvement Proposal: Automated Localization Pipeline for Enablement Content

- **Proposed by:** content-ops-agent
- **Date:** 2026-03-20
- **Status:** proposed
- **Impact:** medium
- **Agents affected:** gtm-deck-agent, bdm-onboarding-digest-agent, territory-research-agent

## Problem

CUBE AI's BD team is international — BDMs cover Western Europe (Hugo), Northern Europe (Zayne), and Southern Europe & Brazil (Sibeli/Cibele). All enablement content (GTM decks, pre-reads, onboarding materials) is currently produced in English only.

When localized materials are needed (e.g. pre-reads in German, French, Portuguese, Spanish), it's handled as a one-off manual request rather than a systematic workflow. This creates delay and inconsistency.

## Proposed Solution

Establish me (content-ops-agent) as the network's designated **localization layer**:

1. **GTM Deck Agent** signals me after each weekly deck is produced
2. I generate translated text-overlay versions for DE (Hugo/Zayne's DACH territory), FR (Hugo's France/Belgium), PT (Sibeli's Portugal/Brazil), ES (Sibeli's Spain)
3. Translated decks land in a shared Google Drive folder alongside the English original
4. **BDM Onboarding Digest Agent** can request localized versions of onboarding documents by messaging me

## Expected Benefits

- EU BDMs receive materials in their prospects' native languages — higher engagement
- Eliminates ad-hoc translation requests to Aaron
- Consistent visual branding across all language versions
- Reuses existing PDF generation pipeline (already proven 2026-03-20)

## Implementation Notes

- I already have a working PDF translation pipeline (PIL + pypdf + custom font rendering)
- GTM Deck Agent needs to send me a message (or I can poll its output folder) when a new deck is ready
- Need Google Drive write access activated on content-ops-agent for output delivery
- Translation quality: I use internal LLM translation — for high-stakes external content, Aaron may want human review

## Owner Decision

{Aaron fills this in — approved/rejected with notes}
