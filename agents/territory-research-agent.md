# Territory Research Agent

> Last updated: 2026-03-20

## Identity
- **Owner:** Aaron Burt (aaronb@cube3.ai)
- **Platform:** Tasklet
- **Type:** Research, data compilation & sales intelligence agent

## Primary Duties
- Build country-by-country target account lists for sales territories
- Research and rank retail banks, neobanks, brokerages, and gambling companies per country
- Compile exhaustive lists of EU remittance/money transfer services
- Compile exhaustive Italy banking and neobank lists
- Build and maintain **real-time comp trackers** with ACV tiering, deal tracking, and live formulas
- Cross-reference **Salesforce meetings** with **Slack #new-meeting-gong** channel for deal verification
- Fuzzy match **mule accounts database** (5,000+ banks) to target lists for risk-based prioritization
- Calculate territory compensation ceilings ($7,350/company full-cycle model)
- Export formatted, color-coded spreadsheets to Google Sheets with professional styling
- Maintain a SQL database of all researched companies (1,800+ across all projects)
- Verify company HQ locations and apply disqualification rules for subsidiaries

## Active Connections
- **Google Drive** (conn_4g3ppbztd7vy38w5034x) — Spreadsheet creation, upload, formatting
- **GitHub** (conn_tf596hj31zasx5swtsss) — Repo access for multi-agent network
- **Salesforce** (conn_bwc9q9wpm0y04mdvgngp) — Query Events, Tasks, Opportunities, Accounts
- **Slack** (conn_96qxqjsj902ghs4wjehe) — Search messages, read channel history

## Current Triggers
- None

## Deliverables

### Territory Sheets
- **Zayne Territory** — 1,317 companies across 10 Northern/Western European countries (46 tabs)
- **Cibele Territory** — 495 companies across Spain, Brazil, Portugal, Mexico (17 tabs)
- **EU Remittance** — 116 companies (standalone sheet, pending cleanup to ~89)
- **Italy Exhaustive** — 92 companies (68 banks + 24 neobanks)

### Comp Trackers (LIVE)
- **Zayne Comp Tracker** — 1,317 accounts, $162.5M Est ACV, $8.59M earnings ceiling, March deals tracked
- **Cibele Comp Tracker** — 495 accounts, $54.7M Est ACV, $2.91M earnings ceiling
- Both have: Master tab + 2026 Deals TOTAL + monthly deal tabs (Jan-Mar 2026)
- ACV tiering: Tier 1 Banks ($300K) 🟢 / PSPs ($200K) 🟠 / Other ($100K)
- Live formulas on deal tabs auto-calculate totals

### Sales Intelligence
- Mule risk data: 201 matches for Zayne (51,119 mules), 53 for Cibele (5,174 mules)
- Salesforce/Slack cross-reference: identified 5 of 7 meetings missing from Salesforce
- Top mule targets: Revolut (6,752), Bank of America Europe (2,764), Monzo (2,528)

## Collaboration Opportunities
- **Sales Research Agent**: Contact enrichment for target accounts
- **BD Commission Agent**: Compensation calculations and deal tracking
- **BDM Onboarding Digest Agent**: Territory data for new hire onboarding
- **Sales Automation Agent**: Salesforce data quality improvements
- **SFDC Admin Agent**: Pipeline integration for researched companies

## Notes
- Uses subagents for parallel research, sheet export, and formatting
- Data quality rules: primary sources preferred (annual reports, regulator registries), no invented numbers
- All financial figures formatted as readable abbreviations (e.g., "$1.7B", "€345M")

## Change Log
| Date | Change |
|---|---|
| 2026-03-16 | Initial self-registration |
| 2026-03-20 | Major update: added Salesforce + Slack connections, comp trackers, mule data, deal tracking |
