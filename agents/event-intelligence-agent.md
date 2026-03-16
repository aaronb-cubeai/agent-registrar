# Event Intelligence Agent

> Last updated: 2026-03-16

## Identity
- **Owner:** Aaron Burt (aaronb@cube3.ai)
- **Platform:** Tasklet
- **Type:** Data extraction, enrichment & CRM integration agent

## Primary Duties
- Extract attendee/speaker contacts from event screen recordings using visual AI (frame extraction + OCR)
- Enrich contacts via BetterContact waterfall enrichment (email, phone, LinkedIn)
- Deduplicate against existing Salesforce records before creating new Contacts linked to Accounts
- Add contacts to Salesforce campaigns (e.g., Intake campaign)
- Patch Salesforce records with enriched fields: AccountId, Title, Phone, LinkedIn_URL__c
- Process EventsAIR event apps for attendee data
- Generate enriched contact spreadsheets for review

## Active Connections
- **BetterContact** — Waterfall enrichment API (email, phone, LinkedIn)
- **Salesforce (REST API integration)** — Contact/Account/Campaign CRUD via Pipedream integration
- **Salesforce (Direct API)** — Direct REST API for batch operations and custom field updates
- **GitHub** — Repository access for self-registration and org chart updates

## Current Triggers
- None

## Notes
- Processes screen recordings by extracting frames at 1fps, subsampling every 3rd frame, and running parallel batch visual extraction
- BetterContact requires wrapped payload format: `{"data": [...], "enrich_email_address": true, "enrich_phone_number": true}`
- Maximum 100 leads per BetterContact API request — larger datasets are automatically batched
- Salesforce LinkedIn field is `LinkedIn_URL__c` (not Description, which is blocked by field-level security)
- Typical enrichment rates: ~80% email, ~75% phone, ~73% LinkedIn
- Has processed 560+ contacts across NYC Financial Crime Summit (March 10 & 11 recordings) and EventsAIR FLSUK26

## Change Log
| Date | Change |
|---|---|
| 2026-03-16 | Initial self-registration |
