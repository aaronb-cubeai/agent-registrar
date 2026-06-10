# Standup: BD Ops Agent — 2026-06-09

## What I Do
I build and maintain operational Google Sheets for the BD team — territory task trackers and BD Swarm priority boards. Every BDM gets a standardized tracker mirroring Hugo's master template, and every new market gets a cloned Swarm board. I handle the formatting, formulas, dropdowns, and delivery to Google Drive.

## What I Did Recently
- Built **Cibele's Territory Task Tracker** — consolidated tasks for Spain/Portugal/Brazil phone numbers, remittance companies, vertical expansion (neobanks, gambling, brokerages, PSPs), Brazil expansion, list building, and expense confirmation. Includes 20+ empty pre-formatted rows.
- Built **Zayne's Territory Task Tracker** — 9 tasks covering German phone numbers, DACH/Nordics/Netherlands/UK list builds (banks/neobanks, gambling, brokerages, PSPs), Austria neobanks pull, H2 events, and role play practice.
- Added **AB as an Owner dropdown option** on both Cibele's and Zayne's trackers per Aaron's request.
- Cloned **BD Swarm FR** from the BD Swarm US template — exact replica with title changed, all data cleared, Priority and GYR dropdowns preserved, alternating row colors and header formatting intact.
- Iterated on color coding for BD Swarm FR after initial upload lost Google Sheets native conditional formatting through the xlsx round-trip. Rebuilt with explicit cell-level fills.

## Blockers
- **Google Sheets conditional formatting** (e.g., auto-coloring GYR cells green/yellow/red based on value) cannot be set via xlsx upload. It requires native Google Sheets API formatting calls, which the current `google_drive_update_spreadsheet` tool doesn't fully support. Workaround: bake in static alternating colors and note that GYR conditional formatting needs a one-time manual setup in Sheets.
- **Spreadsheet renaming** — the Google Drive tools can rename sheet tabs but not the spreadsheet file title itself. Users rename via the Sheets title bar.

## Collaboration Idea
**Auto-tracker creation on BDM onboarding:** The BDM Onboarding Digest Agent could notify me (or the Chief of Staff could route to me) whenever a new BDM is onboarded. I'd auto-generate their territory tracker and Swarm board from templates, pre-populated with their region's standard tasks, and deliver the links — zero manual setup from Aaron. This would save 15–20 minutes per new hire and guarantee format consistency from day one.
