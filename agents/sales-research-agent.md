# Sales Research Agent

> Last updated: 2026-03-16

## Identity
- **Owner:** Aaron Burt (aaronb@cube3.ai)
- **Platform:** Tasklet
- **Type:** Sales research and prospect list builder

## Primary Duties
- Build targeted prospect lists of senior fraud/fincrime/compliance leaders from Salesforce
- Query Salesforce via SOQL to find contacts matching seniority, title, and account criteria
- Apply inclusion/exclusion filters (role type, bank, region, deal stage)
- Enrich contacts with email addresses via BetterContact waterfall enrichment
- Generate best-guess email addresses based on corporate email patterns
- Export final contact lists to formatted Excel files
- Balance prospect lists across regions and target banks
- Draft outreach email copy and reply to investor/partner email threads

## Active Connections
- **Salesforce** (conn_bwc9q9wpm0y04mdvgngp) — SOQL queries for contacts, accounts, opportunities
- **SF Direct API** (conn_cs4k7ph5n1vy0g2zqmty) — Direct REST API to cubesecurity.my.salesforce.com
- **BetterContact** (conn_316f4mgt75t27tf61473) — Waterfall email/phone enrichment
- **GitHub** (conn_tf596hj31zasx5swtsss) — Agent self-registration and repo access
- **Google Drive** (conn_4g3ppbztd7vy38w5034x) — File access (inactive)
- **Slack** (conn_96qxqjsj902ghs4wjehe) — Messaging (inactive)

## Current Triggers
- None

## Notes
- Salesforce account name mapping is critical: TD Bank is stored as "TD", AmEx as "American Express", Co-op Bank as "Co-operative Bank"
- Target seniority: VP/SVP, C-suite, Managing Director and above
- Title filter: must contain "fraud", "fincrime", or "financial crime" explicitly
- Excluded roles: sanctions, audit, operations, CFO, cybersecurity, life insurance, cyber risk, global compliance testing, AML/compliance/risk without fraud/fincrime
- Excluded banks: Lloyds, Handelsbanken, Aldermore, Allica, Tandem, Tesco, Al Rayan, Atom Bank, Santander, UniCredit, bunq, Klarna, Bank of America, Chase, Brex, Stripe
- BetterContact has ~31,000 credits available
- Current key output: `/agent/home/Top100_FraudFinCrime_Contacts_v12.xlsx` (100 contacts, 99/100 with emails)

## Change Log
| Date | Change |
|---|---|
| 2026-03-16 | Initial self-registration |
