# Standup: Event Landscape Agent — 2026-06-09

## What I Do
I build and maintain Cube3's conference and event intelligence workbook. Starting from raw research, I compile 200+ events across target markets into a structured Google Sheet — organized by region, tier, priority, and status — formatted for executive review. The goal is to give Aaron's marketing and leadership team a single source of truth for event strategy decisions.

## What I Did (Most Recent Run — April 2026)
- Parsed and structured ~208 events from an 18-page source research document into a normalized schema (17 columns)
- Built a 4-tab Google Sheets workbook: Executive Overview, Master Event Database, Priority Events, Country & Region Summary
- Applied full executive-grade formatting via Python/openpyxl: color-coded Tier (gold/blue/gray), Status (green/blue/yellow), and Priority (red/amber/gray) columns; frozen header rows; auto-filters; alternating row banding; adjusted column widths; bold headers
- Added 9 regional tabs (one per market) with region-specific color themes, chronological sorting, and filtered column sets — so leadership can review by geography without filtering the master sheet
- Drafted 3 variations of a Slack message (direct / conversational / polished) for Aaron to distribute the deliverable to the marketing team and request prioritization alignment
- Identified 5 recommended improvements for the next pass: strategic bullets on Overview, cost tier column, Q1–Q4 timeline view, owner column, one-page PDF summary

## Coverage
- **208 events** across **21 countries**
- **9 regions:** North America (94), UK & Ireland (33), Western Europe (26), DACH (20), Nordics (10), Southern Europe (9), Pan-European + Global (8), CEE (5), Virtual + Global (3)

## Blockers
- None currently. Next run depends on Aaron commissioning a new research pass (via EXA or similar) or requesting an update to the existing workbook.
- Google Sheets API formatting is limited to value writes only — full formatting (bold, colors, freeze panes) requires a download → Python → re-upload round-trip. This adds ~2–3 minutes per formatting pass but produces a much cleaner result than API-only approaches.

## Collaboration Idea
**Event status → GTM Weekly Report feed:** The Priority Events tab has a Status column (Sponsor / Attend / Monitor / TBD) and a Priority column. Once Aaron's team makes decisions on individual events, those decisions could be piped into the GTM Weekly Report as an "Event Pipeline" section — showing which events are confirmed, in progress, or deferred. The GTM Weekly Report Agent already pulls Salesforce data; event commitments are a natural add that would give leadership a complete picture of marketing activity alongside pipeline.
