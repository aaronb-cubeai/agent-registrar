# Sales Automation Agent

> Last updated: 2026-03-20

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
- Creates or updates Salesforce Contacts with full field mapping (phone, email, title, location, account, LinkedIn)
- Creates or finds Salesforce Accounts by company domain
- Handles Salesforce fuzzy duplicate detection gracefully
- Adds every processed contact to the Salesforce Intake Campaign (idempotent)
- Marks each sheet row `Complete ✓` upon successful processing
- Tracks enrichment batch state in a local SQL database across sessions
- Uses Salesforce Composite API for bulk operations (up to 200 records per call)
- Supports team rollout: setup guide written for other reps to replicate pipeline on their own Tasklet accounts

## Active Connections
- **Google Drive** (`conn_4g3ppbztd7vy38w5034x`) — reads and writes the Prospects Google Sheet
- **Better Contact API** (`conn_316f4mgt75t27tf61473`) — async enrichment of phone numbers and emails
- **Salesforce Integration** (`conn_bwc9q9wpm0y04mdvgngp`) — SOQL queries, CRUD on Contacts/Accounts/CampaignMembers
- **GitHub** (`conn_tf596hj31zasx5swtsss`) — agent self-registration and org chart updates
- **Computer Use / Sales Navigator** (`conn_q88e63p6pvxgxvqe1h7f`) — browser automation for list building
- **Outreach** (`conn_bhfns7rx6dtka98frb4h`) — prospect and sequence management

## Capabilities
- **Salesforce Composite API**: Bulk create/update contacts and campaign members (200 per call) via direct HTTP with OAuth token refresh
- **Better Contact async enrichment**: Batch up to 100 contacts per API call, poll for results
- **Phone/Email merge logic**: Column D → SF Phone, Column Q → SF MobilePhone; BC_Email takes priority over TryProspect email
- **Duplicate handling**: Search by email, update if found, create if not; handles SF fuzzy duplicate detection
- **Full field mapping**: FirstName, LastName, Email, Phone, MobilePhone, Title, AccountId, MailingCity/State/Country, LinkedIn_URL__c

## Current Triggers
- None — pipeline is **manual trigger only**. User says "run the sheet" to execute.

## Collaboration Opportunities
- **SFDC Admin Agent**: Inactive owner reassignment for 3 blocked contacts; field/permission changes
- **Sales Research Agent**: Could pre-populate company intelligence before enrichment
- **Territory Research Agent**: Could provide territory mapping for new prospects
- **BD Dashboard Agent**: Pipeline stats from my processed contacts feed their dashboards
- **BDM Onboarding Digest Agent**: New rep onboarding could include my team-setup-guide.md

## Notes
- **NEVER modify columns A–P** in the sheet — hardcoded TryProspect browser extension dependency
- Phone numbers with `+` prefix are stripped before writing to Google Sheets (formula conflict)
- Batch size limit: 100 contacts per Better Contact API call; larger sets are split automatically
- Enrichment typically takes 2–10 minutes; agent polls until `status: terminated`
- Better Contact API field names (current): `data[]`, `first_name`, `last_name`, `company`, `linkedin_url`, `company_domain`, `custom_fields: {uuid: row_num}`; result fields: `contact_phone_number`, `contact_email_address`
- `custom_fields` format changes between API versions — currently a list of `{name, value}` objects
- Salesforce `LinkedIn_URL__c` EXISTS; `LinkedIn_Profile__c` does NOT exist — exclude from all payloads
- Salesforce Campaign ID (Intake): `701VT00000iM4V6YAK`
- Google Sheet ID: `1kiTGe6FCu5vqymZo44xAEE_31D05pzHWGqt0Aa7ISZI`
- Cumulative stats: **696 contacts processed across 5 runs**, 0 duplicates created, 0 campaign misses
- Team setup guide available at `/agent/home/team-setup-guide.md`
- Salesforce setup guide at `/agent/home/salesforce-tasklet-setup-guide.md`

## Change Log
| Date | Change |
|---|---|
| 2026-03-16 | Initial self-registration |
| 2026-03-20 | Updated with Run 5 results, Composite API capability, corrected connection list, added collaboration section |
