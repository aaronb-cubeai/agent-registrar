# Agent Profile: Banking Market Tracker

- **Agent ID:** banking-market-tracker
- **Display Name:** Banking Market Tracker
- **Workspace:** Aaron's private workspace
- **Owner:** Aaron Burt (aaronb@cube3.ai)
- **Status:** 🟢 Active
- **Last Updated:** 2026-06-09

## Purpose

Owns the end-to-end build and maintenance of the Global Banking Market Tracker workbook — a structured, meeting-ready Excel/Sheets asset covering 19 countries (20 originally; Brazil is currently out of scope). The tracker maps consumer-facing banks, enterprise opportunity status, TAM penetration, and meeting activity across the CUBE3 target banking universe.

## Duties

- **Data ingestion:** Parse and structure raw banking datasets (Google Docs, text exports) into clean tabular data
- **Workbook builds:** Generate and rebuild the Banking Market Tracker (currently v6) with full institution-level data across all in-scope countries
- **In-place updates:** Apply targeted edits to the live spreadsheet — add columns, fix formulas, insert metrics — without rebuilding or losing data
- **QA validation:** Run row count checks and formula audits across all tabs before delivering; ensure Row Count Check tab shows Match = Yes for every country
- **Formula management:** Maintain dynamic TAM Penetration %, Meeting Held %, and Overview roll-up formulas across all country tabs
- **Google Drive sync:** Download source files and upload updated workbooks back to the live Google Drive file (in-place replacement, same file ID)

## Current Deliverable

| Field | Value |
|---|---|
| File | Banking_Market_Tracker_v6.xlsx |
| Google Drive ID | `1ujNiKtdi-atvMIDLQGW5VCTgO7jW0S_K` |
| Institutions tracked | 1,071 across 19 countries |
| Tabs | Overview, Global Market Summary, 20 country tabs, Legend & Sources, Row Count Check |
| Key metrics | TAM Pen %, Meeting Held % (per country + Overview roll-up) |
| Status | ✅ Delivered, live in Google Sheets |

## In-Scope Countries (19)

United States, Canada, Germany, United Kingdom, France, Netherlands, Switzerland, Austria, Sweden, Norway, Denmark, Finland, Belgium, Luxembourg, Ireland, Italy, Spain, Portugal, Czech Republic

## Connections Used

| Connection | ID | Purpose |
|---|---|---|
| Google Drive | `conn_4g3ppbztd7vy38w5034x` | Download source docs, upload workbook |
| GitHub | `conn_tf596hj31zasx5swtsss` | Agent registration, standups |

## Triggers

- **On-demand only** — triggered by Aaron via direct message when dataset updates, new countries are added, or column/formula changes are requested
- No scheduled autonomous runs currently configured

## Key Files (Agent Storage)

| Path | Description |
|---|---|
| `/agent/home/Banking_Market_Tracker_v6.xlsx` | Current deliverable (local copy) |
| `/agent/home/tracker_source.xlsx` | Source downloaded from Google Drive |
| `/agent/home/rebuild_v6.py` | Full rebuild script |
| `/agent/home/banking_dataset.txt` | Original source dataset (4,987 lines) |

## Notes

- Brazil is currently excluded from scope by user instruction
- v1–v5 are superseded; v6 is the canonical version
- TAM Penetration formula had a `#VALUE!` bug in v1–v4 (referencing text label instead of numeric cell) — fixed in v5 and carried forward
- Workbook was migrated from .xlsx to native Google Sheets format in v6 to resolve compatibility issues
