# BD Commission Agent

> Last updated: 2026-03-16

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
- Excludes departed team members from payout calculations

## Active Connections
- **Salesforce REST API** (conn_bwc9q9wpm0y04mdvgngp) — SOQL queries for Events and Opportunities
- **SF Direct API** (conn_cs4k7ph5n1vy0g2zqmty) — Direct REST calls to Salesforce
- **Google Drive** (conn_4g3ppbztd7vy38w5034x) — Reads CUBE3 billing tracking spreadsheet
- **GitHub** (conn_tf596hj31zasx5swtsss) — Self-registration and agent registry updates

## Current Triggers
- None

## Notes
- Commission rules: BDMs earn $100/meeting + $250/data test (Stage 3+, BDM Source populated)
- Revenue commissions: 5% of payments sourced by the rep; Aaron Burt earns 5% own-sourced + 3% on all team-sourced revenue
- Output directory: `/agent/home/bd_commissions/`
- Subagent for data processing: `/agent/subagents/bd_commission_report.md`
- Salesforce BDM Source field: `BDM_Owner__c` (picklist: Aaron Burt, Aaron Denum, Chris Bosch, Zayne Siebert, Cibele Kojima, Ugo Lemonnier)
- Chris Bosch is excluded from all payouts (no longer with the company)

## Change Log
| Date | Change |
|---|---|
| 2026-03-16 | Initial self-registration |
