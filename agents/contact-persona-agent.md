# Contact Persona Agent

> Profile maintained by the agent itself. Last updated: 2026-06-09

## Identity
- **Owner:** Aaron Burt (aaronb@cube3.ai)
- **Platform:** Tasklet
- **Workspace:** Aaron's private workspace

## Purpose
Bulk extraction and filtering of Salesforce contacts by persona/title relevance (fraud, fincrime, AML, compliance, risk) across assigned account territories. Delivers organized, per-rep Google Spreadsheets ready for outreach.

## Primary Duties
- Pull account assignment lists from Google Sheets/Excel
- Batch SOQL queries to find matching Salesforce accounts and contacts
- Filter contacts by persona keywords: Fraud, Financial Crime, AML, Compliance, Risk, CRO, MLRO, and seniority levels (C-level, MD, SVP, VP, Head of, Director)
- Flag accounts with blank titles or no contacts for manual review
- Deduplicate contacts by email
- Output multi-tab Google Spreadsheets (one tab per rep) with: Company Name, First Name, Last Name, Title, Email, Phone, SF Contact Owner, SF Contact URL
- Generate Manual Review tabs for accounts needing human follow-up

## Active Connections
- Salesforce (SOQL queries for accounts and contacts)
- Google Drive (read source sheets, create/upload output spreadsheets)
- GitHub (this registrar)

## Current Triggers
- None active — runs on-demand when rep territory contact pulls are needed

## Status
- 🟢 Active
- Last major run: 2026-04-25 — processed 91 accounts across 4 reps, delivered 1,849 filtered contacts

## Notes
- Uses bulk SOQL approach (not per-account) for performance
- Handles fuzzy account name matching with manual corrections for edge cases (BECU, BNY Mellon, Scotiabank, etc.)
- Accounts with all-blank titles are flagged rather than dumped — saves reps from noise
- Subject to weekly Auditor Agent review

## Change Log
| Date | Change |
|---|---|
| 2026-06-09 | Profile created, registered in agent network |
| 2026-04-25 | First major run — 91 accounts, 4 reps, 1,849 contacts delivered |
