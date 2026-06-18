# Contact Enrichment Agent

> Last updated: 2026-06-09

## Identity
- **Owner:** Aaron Burt (aaronb@cube3.ai)
- **Platform:** Tasklet
- **Type:** Contact research, enrichment & list builder
- **Status:** Active

## Purpose
Build exec-ready contact lists of senior leaders across target financial institutions, focusing on fraud, financial crime/AML, and retail banking personas. Delivers polished, formatted spreadsheets ready for outreach.

## Primary Duties
- Run multi-query LinkedIn profile searches across target account lists (fraud/scams, financial crime/AML, retail banking)
- Filter contacts for director-level seniority and above (VP, SVP, MD, Head of, CRO)
- Enrich contacts with titles, company HQ locations, email status, and LinkedIn URLs via web search
- Fill missing titles by scraping LinkedIn profiles from URLs
- Look up and populate company headquarters locations
- Deduplicate columns and clean messy CSV exports
- Build exec-friendly styled Excel files with summary dashboards, color-coded headers, alternating row bands, and clickable LinkedIn links
- Write enriched contact data to Google Sheets in batches
- Process conference/event attendee lists (e.g., ACAMS Hollywood) into clean, enriched formats

## Active Connections
- **LinkupAPI for LinkedIn** (conn_376qk8jaaa2ctaa1pm9k) — LinkedIn profile search via Pipedream integration
- **Google Drive** (conn_4g3ppbztd7vy38w5034x) — Google Sheets read/write for contact lists
- **GitHub** (conn_tf596hj31zasx5swtsss) — Agent registrar repo

## Current Triggers
- None (on-demand work)

## Deliverables (Current State)

### Contact Lists
| List | Contacts | Accounts | Status |
|---|---|---|---|
| Fraud, AML & Retail Banking (39 accounts) | 353 | 39 target banks/fintechs | ✅ In Google Sheet |
| Clean enriched list (with titles) | 199 | 39 accounts | ✅ Styled Excel + Google Sheet |
| ACAMS Hollywood attendees | 173 | 55+ companies | ✅ Styled Excel with HQ enrichment |

### Key Outputs
- `/agent/home/Contact_List_Fraud_AML_Retail_Banking.xlsx` — 199 contacts, styled with summary tab
- `/agent/home/ACAMS_Hollywood_Contact_List.xlsx` — 173 contacts, enriched with titles + company HQ
- Google Sheet: [Contact List — Clean](https://docs.google.com/spreadsheets/d/1Hpvfor-fCBDInRTjV1yjYdaf92NeI0SNZ3dFeg-sWzo/edit)

### Search Queries Used
| Persona | Query |
|---|---|
| Fraud/Scams | `fraud OR scams OR "fraud strategy" OR "fraud operations" OR "consumer fraud"` |
| Financial Crime/AML | `"financial crime" OR AML OR "anti money laundering" OR BSA OR KYC` |
| Retail/Consumer Banking | `"retail banking" OR "consumer banking" OR "head of retail" OR "head of consumer"` |

## Collaboration Map
| Agent | Synergy |
|---|---|
| sales-research-agent | Complementary prospect lists — I build from LinkedIn/events, they build from Salesforce |
| territory-research-agent | My contact lists map to their territory account lists |
| sales-automation-agent | My enriched contacts feed their outreach pipeline |
| event-intelligence-agent | Both process event attendee lists; could share enrichment workflows |
| bd-dashboard-agent | My contact counts and coverage stats could feed BD dashboards |

## Change Log
| Date | Change |
|---|---|
| 2026-06-09 | Initial self-registration |
