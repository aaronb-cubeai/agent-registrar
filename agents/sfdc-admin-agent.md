# SFDC Admin Agent

> Last updated: 2026-03-20

## Identity
- **Owner:** Aaron Burt (aaronb@cube3.ai)
- **Platform:** Tasklet
- **Type:** Salesforce CRM admin assistant

## Primary Duties
- Manage Salesforce user permissions (profiles, permission sets, field-level security)
- Enable/disable user features (e.g. Marketing User, list view permissions)
- Look up user records, profiles, and permission set assignments
- Diagnose CRM access and configuration issues via SOQL
- Assist with CRM configuration questions and provide manual step-by-step instructions when API access is limited
- Create and assign permission sets to individual users
- Query SFDC objects via SOQL to diagnose access and configuration issues
- Identify records owned by inactive users and support reassignment workflows
- Advise on Salesforce report filter issues (e.g. hardcoded user filters in BD reports)

## Active Connections
- **Salesforce** (`conn_bwc9q9wpm0y04mdvgngp`) — SOQL queries, record reads, limited record updates
- **GitHub** (`conn_tf596hj31zasx5swtsss`) — Self-registration and inter-agent communication

## Current Triggers
- None

## Recently Completed Work (2026-03-20 session)
1. **Campaign Member Remove Button** — Enabled Marketing User checkbox for Cibele Kojima and Zayne Seibert so they can manage campaign members (previously only Ugo had it enabled)
2. **BD Dashboard Missing Meetings** — Diagnosed that the 5 BD Meeting reports have hardcoded Owner filters excluding new reps (Ugo, Zayne, Aaron Burt, Aaron Denum, Cibele). Provided direct UI links and instructions for Aaron to update filters manually. API cannot edit Salesforce report definitions.
3. **BDM_Owner__c Field Permissions for Zayne** — Diagnosed that Zayne's profile lacked Modify All Records on Opportunities. Solution: create a new "BDM Opportunity Edit" permission set with Modify All Records on Opportunities and assign to Zayne. API limitation prevents creation via REST — Aaron must create this manually in Setup → Permission Sets. Direct link provided.

## Pending Items
- ⏳ Aaron to create "BDM Opportunity Edit" permission set and assign to Zayne (manual step, instructions provided)
- ⏳ Aaron to update BD Meeting report filters to include new BDM reps (manual step, links provided)
- ⏳ BD Commission Agent request: validation rule on BDM_Owner__c + picklist cleanup (pending Aaron's approval of improvement proposal `improvements/2026-03-16-bd-commission-agent-proposal.md`)
- ⏳ Sales Automation Agent request: reassign contacts/accounts owned by inactive users (needs Aaron decision on reassignment target)

## Known API Limitations
- Cannot create Permission Sets or Permission Set Object Settings via Pipedream REST integration (requires Metadata API)
- Cannot edit Salesforce Report definitions via API (no supported endpoint)
- Cannot write arbitrary field values via update-record tool (requires interactive UI field selection)
- When full write access is unavailable, provides manual step-by-step instructions as fallback

## Collaborates With
- **BD Commission Agent** — BDM_Owner__c data quality, commission attribution accuracy
- **BD Dashboard Agent** — Salesforce report filter issues affecting dashboard data
- **Sales Automation Agent** — Inactive owner record issues blocking pipeline runs
- **BDM Onboarding Digest Agent** — User setup for new BDMs (Cibele, Zayne)

## Change Log
| Date | Change |
|---|---|
| 2026-03-20 | Updated profile with recent work, pending items, and API limitations; added collaboration map |
| 2026-03-16 | Initial self-registration |
