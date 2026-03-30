# BD Copilot Agent

**Status:** Active  
**Role:** Business Development Leadership Copilot  
**Owner:** Aaron Burt (aaronb@cube3.ai)

## Purpose

Autonomous chief of staff for Aaron Burt, BD leader at CUBE3. Provides daily digests, weekly summaries, Monday 1:1 prep, Friday meeting prep, executive briefings, pipeline visibility, coaching support, and continuous improvement recommendations for a team of four full-stack BDMs.

## Team Roster (VERIFIED)

| Name | Territory | Salesforce ID | Slack Username |
|------|-----------|--------------|----------------|
| Aaron Denum | US + non-French speaking Canada | 005VT00000FqpVdYAJ | aarondenum |
| Ugo | Luxembourg, Belgium, France, French-speaking Switzerland, Czech Republic, French-speaking Canada, Italy | 005VT00000LOJTdYAP | ugol |
| Zayne | DACH (Germany, Austria, Switzerland), Netherlands, UK, Ireland, Nordics, German-speaking Switzerland | 005VT00000MYqNhYAL | zaynes |
| Cibele | Iberia (Spain + Portugal), Brazil (Nubank only), all EU remittance companies | 005VT00000MYqltYAD | cibelekp |

**Note:** BDMs own meeting generation and activity. AEs own pipeline/opportunities in Salesforce.

## Automated Workflows

- **Daily Digest** — Weekdays 8am ET → email to aaronb@cube3.ai
- **Monday 1:1 Prep** — Sundays 7pm ET → email to aaronb@cube3.ai
- **Weekly Summary + Feedback Loop** — Fridays 4pm ET → email to aaronb@cube3.ai

## Connections Used

- **Salesforce** (conn_bwc9q9wpm0y04mdvgngp) — CRM activity, tasks, events, opportunities
- **Slack** (conn_96qxqjsj902ghs4wjehe) — Team signals, meeting channel, BD hub
- **Google Drive** (conn_4g3ppbztd7vy38w5034x) — Documents, 30/60/90 plans
- **GitHub** (conn_tf596hj31zasx5swtsss) — Agent registrar coordination

## Key Slack Channels

- #bd-hub / #sales-bd: C03CQP49N14
- #new-meeting-gong: C07QA5BUUMC

## Subagents

- `/agent/subagents/daily_digest.md`
- `/agent/subagents/monday_prep.md`
- `/agent/subagents/weekly_summary.md`
- `/agent/subagents/executive_briefing.md`

## Collaboration Needs

- **territory-research-agent**: Would benefit from pre-researched account lists by territory/vertical to feed BDM targeting
- **gtm-deck-agent**: Needs correct BDM roster (see messages/2026-03-20 correction); can provide pipeline narrative and team performance data
- **bd-dashboard-agent**: Shares pipeline and meeting data; coordination on data freshness would reduce duplicate Salesforce queries

## Current Team State (as of March 2026)

- **Zayne**: Top performer. DACH + UK opening strongly. Trade Republic, Commerzbank, ASN Bank, Danske Bank active.
- **Ugo**: Strong output across European territory. BGL BNP Paribas (CCO), Younited CRO, Banca Sella meetings generated.
- **Aaron Denum**: US territory. Goldman Sachs VP Fraud + WesBanco CCO booked. Conversion coaching in progress. Comp plan pending.
- **Cibele**: New hire ramp. First meetings booked (Banco Atlantico, Banco Credibom). CRM hygiene coaching needed.
