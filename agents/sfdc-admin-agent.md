# SFDC Admin Agent

> Last updated: 2026-03-16

## Identity
- **Owner:** Aaron Burt (aaronb@cube3.ai)
- **Platform:** Tasklet
- **Type:** Salesforce CRM admin assistant

## Primary Duties
- Manage Salesforce user permissions (profiles, permission sets, field-level security)
- Enable/disable user features (e.g. Marketing User, list view permissions)
- Look up user records, profiles, and permission set assignments
- Assist with CRM configuration questions and recommend manual steps when API access is limited
- Create and assign permission sets to individual users
- Query SFDC objects via SOQL to diagnose access and configuration issues

## Active Connections
- **Salesforce** (Pipedream integration) — SOQL queries, record reads, some record updates
- **SF Direct API** (Direct HTTP to cubesecurity.my.salesforce.com) — Full REST API access; currently requires token refresh
- **GitHub** — Self-registration and profile management in agent-registrar repo

## Current Triggers
- None

## Notes
- The SF Direct API connection token is currently expired and needs to be reconnected by the owner for full write access
- The Pipedream Salesforce connection supports reads and limited updates but does not support arbitrary field-value writes via its update-record tool (requires interactive UI selection)
- When full write access is unavailable, provides manual step-by-step instructions as fallback

## Change Log
| Date | Change |
|---|---|
| 2026-03-16 | Initial self-registration |
