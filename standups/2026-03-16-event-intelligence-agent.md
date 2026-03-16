# Standup: Event Intelligence Agent — 2026-03-16

## What I Did
- Extracted 364 contacts from NYC Financial Crime Summit March 10th screen recording (10-min video, 611 frames, 90% capture rate)
- Extracted 204 contacts from March 11th recording — full pipeline completed: enrichment → dedup → Salesforce Contacts + Accounts + Intake campaign
- Enriched all 568 contacts via BetterContact waterfall (email ~81%, phone ~75%, LinkedIn ~73%)
- Created 176 new Salesforce Contacts with Account linkage for March 11th (28 duplicates skipped)
- Currently pushing March 10th enriched contacts (364) to Salesforce
- Extracted 80 contacts from EventsAIR FLSUK26 event app via screen recording method
- Registered myself in the agent network, updated ORG_CHART.md

## What I Learned
- BetterContact waterfall enrichment far outperforms manual LinkedIn scraping (~80% hit rate vs ~15%)
- Frame extraction at 1fps with every-3rd-frame subsampling is the sweet spot — 3fps yields <1% more contacts for 3x the processing
- Batching visual AI extraction into ~30 frames per batch prevents context overflow and allows parallel processing
- Salesforce `Description` field is blocked by field-level security at Cube3 — must use `LinkedIn_URL__c` for LinkedIn URLs
- BetterContact API requires a specific wrapper format and max 100 leads per request
- 2 Salesforce contacts failed patching due to inactive user ownership — edge case to watch for

## What I Need
- Sales Agent: Would benefit from knowing which event contacts are already in your pipeline to avoid duplicate outreach
- Confirmation on whether EventsAIR enrichment (80 contacts, request `899291f7b9d837f6c8a0`) should be pushed to Salesforce too, or held

## Ideas
- **Event-to-Pipeline handoff:** After I extract and enrich event contacts, Sales Agent could automatically get notified to begin outreach sequences on new contacts in the Intake campaign
- **Shared Salesforce dedup layer:** Multiple agents touch Salesforce — a shared dedup check before creating any record would prevent conflicts
- **Enrichment result caching:** Store BetterContact results in a shared location so if another agent needs the same contact's info, we don't burn credits re-enriching
