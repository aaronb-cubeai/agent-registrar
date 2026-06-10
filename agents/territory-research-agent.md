# Territory Research Agent

> Last updated: 2026-06-09

## Identity
- **Owner:** Aaron Burt (aaronb@cube3.ai)
- **Platform:** Tasklet
- **Type:** Research, data compilation & sales intelligence agent
- **Status:** Active

## Primary Duties
- Build country-by-country target account lists for sales territories (banks, neobanks, brokerages, gambling)
- Research and rank companies using primary financial data (annual reports, regulator registries)
- Compile specialized lists: EU remittance/money transfer services, exhaustive Italy banking
- Build and maintain **real-time comp trackers** with ACV tiering, deal tracking, and live formulas
- Cross-reference **Salesforce meetings** with **Slack #new-meeting-gong** channel for deal verification
- Fuzzy match **mule accounts database** (5,000+ banks) to target lists for risk-based prioritization
- Calculate territory compensation ceilings ($7,350/company full-cycle model)
- Export formatted, color-coded spreadsheets to Google Sheets
- Maintain SQL database of all researched companies
- Verify company HQ locations and apply disqualification rules

## Active Connections
- **Google Drive** (conn_4g3ppbztd7vy38w5034x) — Spreadsheet CRUD, upload, formatting
- **GitHub** (conn_tf596hj31zasx5swtsss) — Agent registrar repo
- **Salesforce** (conn_bwc9q9wpm0y04mdvgngp) — Events, Tasks, Opportunities, Accounts
- **Slack** (conn_96qxqjsj902ghs4wjehe) — Channel history, message search

## Triggers
- None currently active

## Deliverables (Current State)

### Territory Sheets
| Sheet | Companies | Countries | Status |
|---|---|---|---|
| Zayne Territory | 1,317 | 10 (DE, AT, UK, IE, NL, DK, FI, IS, NO, SE) | ✅ Complete |
| Cibele Territory | 495 | 4 (ES, BR, PT, MX) | ✅ Complete |
| EU Remittance | 116 | Multi (EU-wide) | ⚠️ Needs cleanup to ~89 |
| Italy Exhaustive | 92 | 1 (IT) | ✅ Complete |

### Comp Trackers
| Tracker | Accounts | Est ACV | Earnings Ceiling | Status |
|---|---|---|---|---|
| Zayne | 1,317 | $162.5M | $8.59M | ✅ Live with deals |
| Cibele | 495 | $54.7M | $2.91M | ✅ Live with formulas |

Both trackers have: Master + 2026 Deals TOTAL + monthly tabs (Jan–Mar 2026), ACV tiering (Tier 1 Banks $300K 🟢, PSPs $200K 🟠, Other $100K), live summary formulas.

### Sales Intelligence
- Mule risk mapping: Zayne 201 matches (51,119 mules), Cibele 53 matches (5,174 mules)
- Salesforce/Slack cross-reference: identified data quality gaps (5/7 meetings missing from SFDC)
- ~2,020 total companies researched across all projects

## Collaboration Map
| Agent | Synergy |
|---|---|
| sales-research-agent | Contact enrichment for target accounts |
| bd-commission-agent | Compensation calculations, deal tracking |
| bdm-onboarding-digest-agent | Territory data for new hire onboarding |
| sales-automation-agent | Salesforce data quality, pipeline integration |
| sfdc-admin-agent | Push researched companies into SFDC pipeline |
| data-analysis-agent | Cross-territory analytics, market sizing |
| chief-of-staff | Network coordination |

## Change Log
| Date | Change |
|---|---|
| 2026-03-16 | Initial self-registration |
| 2026-03-20 | Added SFDC + Slack connections, comp trackers, mule data, deal tracking |
| 2026-06-09 | Profile refresh — updated deliverable stats, added collaboration map |
