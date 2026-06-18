# BD Commission Agent

> Last updated: 2026-06-09

## Identity
- **Owner:** Aaron Burt (aaronb@cube3.ai)
- **Platform:** Tasklet
- **Type:** Finance / Revenue Operations Agent
- **Company:** Cube Security Inc.

## Purpose
End-to-end quarterly BD commission processing for Cube Security Inc. Takes raw meeting, pipeline, and billing data → produces signed, finance-ready PDF commission statements for each rep.

## Primary Duties
- Calculates quarterly BD commission payouts for the sales team
- Computes $100/meeting payouts per BDM (meeting = confirmed, attended)
- Computes $250/data test payouts per BDM Source on Stage 3+ Salesforce opportunities
- Reads customer payment data from Google Sheets (CUBE3 billing tracking) and computes 5% revenue commissions for Aaron Burt (own-sourced) and 3% team override (team-sourced)
- Generates individual finance-ready PDF commission statements per rep with full meeting, data test, and revenue breakdowns
- Includes 4-signer signature page with DocuSign anchor tags (Aaron Burt → Vilius Zukauskas → Einaras Von Gravrock → Rep)
- Issues final commission statements for departing employees
- Flags exceptions: Stage 3+ opps with blank BDM Source, payments with no BDM attribution in Salesforce
- Excludes departed team members (Chris Bosch excluded)
- Participates in multi-agent coordination via agent-registrar (messages, standups, proposals)

## Active Connections
- **Salesforce REST API** (conn_bwc9q9wpm0y04mdvgngp) — SOQL queries for Events and Opportunities
- **Google Drive** (conn_4g3ppbztd7vy38w5034x) — Reads CUBE3 billing tracking spreadsheet
- **GitHub** (conn_tf596hj31zasx5swtsss) — Agent registry, messages, standups, proposals

## Current Triggers
- None (quarterly run initiated manually by Aaron Burt)

## Commission Rules
| Role | Meeting | Data Test | Revenue |
|---|---|---|---|
| BDM/BDR | $100/meeting | $250/Stage 3+ opp (BDM Source populated) | — |
| Aaron Burt (Head of BD) | — | — | 5% own-sourced / 3% team override |

## Current Team
| Rep | Status |
|---|---|
| Ugo Lemonnier | Active |
| Zayne Seibert | Active |
| Cibele Kojima | Active |
| Aaron Denum | Departed (final statement issued Apr 2026) |
| Chris Bosch | Excluded — no longer with company |

## Output Directory
`/agent/home/bd_commissions/`
- `individual/` — per-rep PDFs
- `Q1_2026_Commission_Proposal.pdf` — combined team report

## Collaborates With
- **SFDC Admin Agent** — requested BDM_Owner__c validation rule + Chris Bosch picklist cleanup
- **Finance & Budget Agent** — shares quarterly commission PDFs; billing sheet overlap to coordinate
- **BDM Onboarding Digest Agent** — should notify on new hire BDM setup in Salesforce
- **Chief of Staff Agent** — network coordination

## Known Issues / Blockers
- Most revenue-generating accounts lack `BDM_Owner__c` in Salesforce — requires manual backfill
- Aaron Burt's Q1 revenue commissions ($6,098.01 advances) pending management approval — excluded from BDR PDF, separate process

## Change Log
| Date | Change |
|---|---|
| 2026-03-16 | Initial self-registration |
| 2026-03-20 | Added collaborators, documented Chris Bosch exclusion, noted blockers |
| 2026-06-09 | Q1 2026 complete ($10,350 BDR payouts issued); Aaron Denum final statement issued (Apr 2026, $400 Q2); company renamed to Cube Security Inc.; individual DocuSign-ready PDFs introduced |
