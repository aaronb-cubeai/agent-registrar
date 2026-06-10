# Standup: Contact Enrichment Agent — 2026-06-09

## What I Did
- Built a contact list of 353 people across 39 target accounts (Goldman Sachs, RBC, Huntington, PNC, TD Bank, etc.) using LinkedIn profile search via LinkupAPI
- Ran 3 search queries per account: fraud/scams, financial crime/AML, retail/consumer banking
- Filtered for director-level and above (VP, SVP, MD, Head of, CRO)
- Wrote all 353 contacts to a shared Google Sheet in 8 batches
- Enriched a 199-contact export: filled 79 of 81 missing titles (99% coverage) using LinkedIn URL web lookups
- Built styled Excel files with navy headers, orange accents, alternating row bands, color-coded email status, clickable LinkedIn links, frozen headers, and auto-filters
- Added a Summary dashboard tab with stat cards, seniority breakdown, and top-20 company rankings
- Processed an ACAMS Hollywood conference attendee list (173 contacts): cleaned 33 columns down to 15, enriched 10 missing titles, added HQ locations for 60 companies (99% coverage)

## What I Learned
- LinkupAPI profile endpoint returns empty data for non-connected LinkedIn profiles — web search (`site:linkedin.com/in/...`) is more reliable for title lookups
- Google Sheets API interprets `+1` phone numbers as formulas — must prepend with apostrophe to force text format
- Conference attendee CSVs are messy: 4 duplicate columns, empty fields, inconsistent formatting — always analyze structure before processing
- Company HQ lookup via web search has excellent coverage (~99%) for financial institutions

## Cross-Agent Observations
- **sales-research-agent** builds prospect lists from Salesforce with BetterContact enrichment — we could combine our LinkedIn-sourced contacts with their Salesforce-verified data to create a master prospecting database with higher coverage
- **territory-research-agent** maintains territory account lists — my 39-account target list overlaps with their territories; syncing would avoid duplicate outreach
- **event-intelligence-agent** also processes event attendee lists — we should share enrichment methods (I found web search beats API for LinkedIn title lookups)

## What I Need
- No blockers currently
- Would benefit from access to BetterContact for email/phone enrichment on new contact lists (currently leaving email/phone blank when not in source data)

## Ideas
- **Unified contact deduplication pipeline:** Create a shared workflow where my LinkedIn-sourced contacts, sales-research-agent's Salesforce contacts, and event-intelligence-agent's event contacts are merged and deduplicated before outreach. This would prevent the same prospect from getting hit 3 times by different workflows. Could use a shared SQL table or Google Sheet as the master record.
