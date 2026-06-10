# Standup — Data Analysis Agent
**Date:** 2026-06-09 (updated)

---

## What I Do
I am Aaron's primary ad-hoc data agent. I handle direct conversational requests that don't belong to a specialized agent — data analysis, file processing, live spreadsheet management, one-off research, and report generation. I also maintain the agent-registrar on behalf of Aaron.

---

## What I've Been Working On

### North America Bank Prospecting Pipeline
- **Source analysis:** Parsed the "North America - Overview" Excel workbook (4 tabs: US Banks, Canada, US Neobanks, US Credit Unions — 226 total institutions). Identified 201 with no active opportunity.
- **Built interactive review app:** Created a filterable Instant App for Aaron to review all 201 no-opp banks before adding to outreach sheet. Filters by category, meeting status, and search.
- **CUBE3 x Dig Ventures spreadsheet update:** Added 148 qualified no-opp banks starting at row 198. Applied filtering rules (banks under $20B assets excluded unless 30+ mules). Tagged all entries with "AB" as BDM Owner.
- **All 19 US Neobanks added** separately (no filter applied) per Aaron's request.
- **Formatting & QA:**
  - Fixed row heights, borders, font styling, and alternating row shading to match existing rows
  - Extended data validation dropdowns (BDM Owner, Warm Contact, Status) to all new rows
  - Added new "Priority Ranking" column with 1-4 dropdown
  - Scrubbed 6 duplicates (3 exact, 3 near-match: SECU, Golden 1/Golden One, America First)

### LinkedIn Company Name Enrichment
- **289 banks enriched** with LinkedIn company page names via batch web search (10 parallel batches of ~30)
- **288 high-confidence matches**, 3 medium, 3 low (kept original name)
- Notable rebrand catches: Credorax → Shift4, Boursorama → BoursoBank, Aspiration → GreenFi, Collector Bank → Norion Bank, HomeStreet → Mechanics Bank
- Added as new Column B ("LinkedIn Name") next to Target Bank

### LATAM Mule Account Intelligence (earlier)
- Completed full update of master Google Sheets workbook (1,021 records, 5 countries, 6 tabs)
- Established QA discipline: backup-first, read-back-after-write, pre/post totals reconciliation

---

## Blockers
- **Excel formatting limitations via openpyxl:** Data validation ranges and row formatting need to be carefully managed when inserting/deleting rows. Duplicate removal shifted row indices, which caused misalignment in LinkedIn name mapping. Resolved by switching from row-index matching to name-based matching.
- **LinkedIn name accuracy for smaller banks:** ~1% of banks had no LinkedIn presence or ambiguous results. Flagged as low-confidence for manual review.

---

## Cross-Agent Observations
- **Territory Research Agent** could benefit from the LinkedIn name mapping dataset I built — 289 NA bank/fintech names mapped to LinkedIn pages with confidence scores. Could be shared as a reference lookup.
- **Sales Automation Agent** — the cleaned CUBE3 x Dig Ventures list (339 rows, deduplicated, LinkedIn-enriched, priority-ranked) is ready to feed into outreach sequences once Aaron prioritizes.
- **BD Dashboard Agent** — the Priority Ranking column (P1-P4) we added could drive dashboard filtering for high-priority NA targets.

---

## What I Need
- Aaron to define P1-P4 priority criteria and tag banks accordingly — this will unlock downstream automation.
- Confirmation on whether to extend LinkedIn enrichment to the European bank rows (1-197) in the CUBE3 x Dig Ventures sheet.

---

## Ideas
- **Automated priority scoring:** Build a scoring model that auto-suggests P1-P4 based on total assets, mule count, meeting status, and warm contact availability. Aaron reviews and confirms, saving manual tagging time.
- **Cross-agent LinkedIn name cache:** Store the 289 LinkedIn name mappings in a shared workspace file so Territory Research, Sales Research, and Sales Automation agents can all reference it without re-searching.
