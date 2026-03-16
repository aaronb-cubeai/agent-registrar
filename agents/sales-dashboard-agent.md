# Sales Dashboard Agent

> Last updated: 2026-03-16

## Identity
- **Owner:** Aaron Burt (aaronb@cube3.ai)
- **Platform:** Tasklet
- **Type:** Data & Analytics Agent — live sales intelligence dashboard

## Primary Duties
- Build and maintain the Cube Security Sales Dashboard (dark navy, 11-tab app)
- Query Salesforce (Opportunity object) for live pipeline, funnel, rep, and segment metrics
- Wire all KPI tiles, charts, and tables to real SFDC data via SOQL
- Support drilldowns on every metric to underlying opportunity records
- Iterate on UI/UX to match design specs (screenshots provided by owner)
- Package and prepare deployment artifacts (zip, proxy, README) for dev handoff
- Debug and fix SOQL field errors as Salesforce schema evolves
- Register and maintain this agent profile in the org registry

## Active Connections
- **Salesforce** (conn_bwc9q9wpm0y04mdvgngp) — SOQL search, field introspection
- **SF Direct API** (conn_cs4k7ph5n1vy0g2zqmty) — Direct REST calls to cubesecurity.my.salesforce.com
- **GitHub** (conn_tf596hj31zasx5swtsss) — Push agent profiles and deployment code

## Current Triggers
- None

## Notes
- The dashboard app lives at `/agent/home/apps/sales-dashboard/` and is pinned in the Tasklet sidebar
- All Salesforce data pulls from `cubesecurity.my.salesforce.com` (Cube Security org)
- Custom SF fields in use: `Segment__c`, `BDM_Owner__c`, `First_Meeting_Date__c`, `Loss_Reason__c`, `Discovery_Completed__c`, `Budget_Confirmed__c`, `ROI_Analysis_Completed__c`
- A deployment package (`sales-dashboard-deploy.zip`) is available for dev handoff — includes frontend (Vite/React/TS), Node.js proxy, and full deploy instructions
- When deployed externally, the app requires a backend proxy to hold SF OAuth credentials
- Owner can request code changes at any time; dev resource handles redeployment

## Change Log
| Date | Change |
|---|---|
| 2026-03-16 | Initial self-registration |
