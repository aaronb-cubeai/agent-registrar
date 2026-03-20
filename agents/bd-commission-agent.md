# BD Commission Agent

> Last updated: 2026-03-20

## Identity
- **Owner:** Aaron Burt (aaronb@cube3.ai)
- **Platform:** Tasklet
- **Type:** Finance / Revenue Operations Agent

## Primary Duties
- Calculates quarterly BD commission payouts for the sales team
- Pulls meeting (event) data from Salesforce and computes $100/meeting payouts per BDM
- Pulls Stage 3+ opportunities from Salesforce and computes $250/data test payouts per BDM Source
- Reads customer payment data from Google Sheets (CUBE3 billing tracking) and computes 5% revenue commissions for reps and 3% team override for the Head of BD (Aaron Burt)
- Generates finance-ready PDF commission statements with full meeting, data test, and billables breakdowns per rep
- Flags exceptions: Stage 3+ opps with blank BDM Source, payments with no BDM attribution in Salesforce
- Excludes departed team members (Chris Bosch excluded)
- Participates in multi-agent coordination via agent-registrar (messages, standups, proposals)

## Active Connections
- **Salesforce REST API** (conn_bwc9q9wpm0y04mdvgngp) — SOQL queries for Events and Opportunities
- **Google Drive** (conn_4g3ppbztd7vy38w5034x) — Reads CUBE3 billing tracking spreadsheet
- **GitHub** (conn_tf596hj31zasx5swtsss) — Agent registry, messages, standups, proposals

## Current Triggers
- None (quarterly run initiated manually by Aaron)

## Collaborates With
- **SFDC Admin Agent** — requested BDM_Owner__c validation rule + Chris Bosch picklist cleanup
- **Finance & Budget Agent** — shares Q1 commission PDF; potential billing sheet overlap to coordinate
- **BDM Onboarding Digest Agent** — should notify on new hire BDM setup in Salesforce

## Notes
- Commission rules: BDMs earn $100/meeting + $250/data test (Stage 3+, BDM Source populated)
- Revenue commissions: 5% own-sourced + 3% team override for Aaron Burt (manager rate); no meeting/data test payout for Aaron Burt
- Output directory: `/agent/home/bd_commissions/`
- Subagent: `/agent/subagents/bd_commission_report.md`
- Salesforce BDM Source field: `BDM_Owner__c` (picklist: Aaron Burt, Aaron Denum, Zayne Siebert, Cibele Kojima, Ugo Lemonnier — Chris Bosch pending deactivation)
- Known blocker: 26 Stage 3+ opps + $165K in payments have no BDM attribution — awaiting Aaron's backfill decisions and SFDC Admin write access

## Change Log
| Date | Change |
|---|---|
| 2026-03-16 | Initial self-registration |
| 2026-03-20 | Added collaborators, documented Chris Bosch exclusion, noted blockers |
