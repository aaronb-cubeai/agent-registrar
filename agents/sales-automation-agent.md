# Sales Automation Agent

> Last updated: 2026-03-16

## Identity
- **Owner:** Aaron Burt (aaronb@cube3.ai)
- **Platform:** Tasklet
- **Type:** Sales pipeline automation agent

## Primary Duties
- Reads new prospect rows from a Google Sheet (added by reps via TryProspect browser extension)
- Submits prospects to Better Contact API (async batch enrichment) for phone and email discovery
- Polls Better Contact until results are complete, writes enriched data back to sheet (cols Q–T)
- Applies merge logic: intelligently combines TryProspect and Better Contact phone/email data
- Deduplicates Salesforce contacts (search by email before create/update)
- Creates or updates Salesforce Contacts with full field mapping (phone, email, title, location, account)
- Creates or finds Salesforce Accounts by company domain
- Handles Salesforce fuzzy duplicate detection gracefully
- Adds every processed contact to the Salesforce Intake Campaign (idempotent)
- Marks each sheet row `Complete ✓` upon successful processing
- Tracks enrichment batch state in a local SQL database across sessions
- Supports team rollout: setup guide written for other reps to replicate pipeline on their own Tasklet accounts

## Active Connections
- **Google Drive** (`conn_4g3ppbztd7vy38w5034x`) — reads and writes the Prospects Google Sheet
- **Better Contact API** (`conn_316f4mgt75t27tf61473`) — async enrichment of phone numbers and emails
- **Salesforce Direct API** (`conn_cs4k7ph5n1vy0g2zqmty`) — full CRUD on Contacts, Accounts, CampaignMembers
- **Salesforce Integration** (`conn_bwc9q9wpm0y04mdvgngp`) — supplemental Salesforce operations
- **GitHub** (`conn_tf596hj31zasx5swtsss`) — agent self-registration and org chart updates
- **Computer Use / Sales Navigator** (`conn_q88e63p6pvxgxvqe1h7f`) — browser automation for list building
- **Outreach** (`conn_bhfns7rx6dtka98frb4h`) — prospect and sequence management
- **Slack** (`conn_96qxqjsj902ghs4wjehe`) — future: AI Sales Command Center notifications

## Current Triggers
- None — pipeline is **manual trigger only**. User says "run the sheet" to execute.

## Notes
- **NEVER modify columns A–P** in the sheet — hardcoded TryProspect browser extension dependency
- Phone numbers with `+` prefix are stripped before writing to Google Sheets (formula conflict)
- Batch size limit: 100 contacts per Better Contact API call; larger sets are split automatically
- Enrichment typically takes 2–10 minutes; agent polls until `status: terminated`
- Better Contact API field names (current): `data[]`, `first_name`, `last_name`, `company`, `linkedin_url`, `company_domain`, `custom_fields.row_index`; result fields: `contact_phone_number`, `contact_email_address`
- Salesforce Campaign ID (Intake): `701VT00000iM4V6YAK`
- Google Sheet ID: `1kiTGe6FCu5vqymZo44xAEE_31D05pzHWGqt0Aa7ISZI`
- Cumulative stats: ~356 contacts processed, 0 duplicates created, 0 campaign misses across 3 runs
- Team setup guide available at `/agent/home/team-setup-guide.md`

## Change Log
| Date | Change |
|---|---|
| 2026-03-16 | Initial self-registration |
