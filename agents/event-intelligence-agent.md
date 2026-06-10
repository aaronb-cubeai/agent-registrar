# Event Intelligence Agent

> Last updated: 2026-06-09

## Identity
- **Owner:** Aaron Burt (aaronb@cube3.ai)
- **Platform:** Tasklet
- **Type:** Event contact extraction, enrichment & CRM integration agent

## Primary Duties
- Extract attendee/speaker contacts from event screen recordings using visual AI (frame extraction + OCR)
- Extract contacts from event PDFs and attendee lists
- Enrich contacts via BetterContact waterfall enrichment (email, phone, LinkedIn)
- Deduplicate against existing Salesforce records before creating new Contacts linked to Accounts
- Add contacts to Salesforce campaigns with proper Account mapping
- Format and push enriched data to Google Sheets (prettified, text-formatted phones, clickable links)
- Scout side events and networking opportunities at upcoming conferences
- Process EventsAIR event apps for attendee data

## Active Connections
- **BetterContact** (`conn_316f4mgt75t27tf61473`) — Waterfall enrichment API (email, phone, LinkedIn). ~34,500 credits remaining.
- **Salesforce REST API** (`conn_bwc9q9wpm0y04mdvgngp`) — Contact/Account/Campaign CRUD via Pipedream integration (active)
- **Salesforce Direct API** (`conn_cs4k7ph5n1vy0g2zqmty`) — Direct REST API for batch operations and custom field updates (⚠️ expired, needs reauthorization)
- **Google Drive** (`conn_4g3ppbztd7vy38w5034x`) — Spreadsheet creation and formatting
- **GitHub** (`conn_tf596hj31zasx5swtsss`) — Repository access for self-registration and org chart updates

## Current Triggers
- None — all work is manual/on-demand batch processing

## Completed Work

### Fraud Fight Club 2026
- Extracted 202 unique contacts from event video
- Enriched all via BetterContact (3 batches)
- Pushed to Google Sheet with full prettification (dark navy header, alternating rows, frozen header, filters, clickable links, text-formatted phones)
- Created 87 new Salesforce Contacts + matched 31 existing = 164 in "Fraud Fight Club 2026" campaign (`701VT00000m0eOPYAY`)
- **Pending:** AccountId and LinkedIn_URL__c patching for 164 contacts (blocked by expired Direct API connection)
- ~38 contacts skipped (no email or duplicate leads)

### NYC Financial Crime Summit — March 11
- Extracted 204 contacts from screen recording
- Enriched and created 176 new Salesforce Contacts in Intake campaign (`701VT00000iM4V6YAK`)
- ✅ Fully complete

### NYC Financial Crime Summit — March 10
- Extracted 364 contacts, enriched via BetterContact (4 batches)
- Enriched CSV delivered to user
- **Pending:** Salesforce import (subagent built, not yet run)

### Global Fraud Summit 2026
- Extracted 1,244 participants from PDF
- Formatted in prettified Google Sheet (`1zSyjwplenNu7_63IDCKlq9Bm09If08FWBEU6yUnKDFM`)

### EventsAIR (FLSUK26)
- Extracted 80 contacts from event app screen recording
- BetterContact enrichment submitted (status pending)

### ACAMS Hollywood 2026 (Ad-hoc Research)
- Scouted side events and networking opportunities for April 20-22 conference
- Found and confirmed Chainalysis Happy Hour (Apr 21, Tiki Tiki)
- Mapped all official ACAMS receptions
- Identified likely private events from major sponsors

## Technical Notes
- Processes screen recordings by extracting frames at 1fps, subsampling every 3rd frame, and running parallel batch visual extraction
- BetterContact requires wrapped payload format: `{"data": [...], "enrich_email_address": true, "enrich_phone_number": true}`
- Maximum 100 leads per BetterContact API request — larger datasets are automatically batched
- Salesforce LinkedIn field is `LinkedIn_URL__c` (not Description, which is blocked by field-level security)
- Google Sheets phone numbers must be prefixed with `'` to avoid formula interpretation
- For large Salesforce imports (100+ records), uses bulk parallel batch subagents with account pre-mapping (~1,925 existing accounts cached)
- Typical enrichment rates: ~80% email, ~75% phone, ~73% LinkedIn
- Total contacts processed to date: 1,900+

## Known Blockers
- **Salesforce Direct API expired** — cannot PATCH arbitrary fields (AccountId, LinkedIn_URL__c) on existing contacts. Pipedream `update-record` tool doesn't support setting arbitrary field values. Reauthorization failed interactively.
- **No automated triggers** — all event processing is manual. Could benefit from a trigger on Google Drive or email for new event files.

## Change Log
| Date | Change |
|---|---|
| 2026-03-16 | Initial self-registration |
| 2026-06-09 | Major update — added FFC, GFS, ACAMS work; updated connections, stats, blockers |
