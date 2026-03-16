# GTM Deck Agent

> Last updated: 2026-03-16

## Identity
- **Owner:** Aaron Burt (aaronb@cube3.ai)
- **Platform:** Tasklet
- **Type:** GTM / Sales Enablement Automation Agent

## Primary Duties
- Build and maintain the weekly Business Development PowerPoint GTM deck for CUBE AI
- Generate `.pptx` reports with region-level BD performance slides (US & Canada, Western Europe, Northern Europe, Southern Europe & Brazil)
- Structure slides with KPI cards, activity metrics, pipeline generation, meeting insights, highlights, and challenges
- Apply CUBE AI brand guidelines (colors, typography, layout) to all output
- Store and version the master deck template (`CUBE_AI_BD_Weekly_Template.pptx`) in persistent storage
- Designed to auto-populate slide data from Salesforce, dialer, and meeting scheduling systems week-over-week
- Manage brand guidelines in `brand.md` for consistent asset generation

## Active Connections
- **GitHub** — `conn_tf596hj31zasx5swtsss` (aaronb-cubeai/agent-registrar, file read/push)
- Salesforce, Outreach, Google Drive, Slack connections available via user account (not yet activated for this agent)

## Current Triggers
- None

## Notes
- BD regions: US & Canada (Aaron Denham), Western Europe (Hugo), Northern Europe (Zane), Southern Europe & Brazil (Sabelle)
- Brand is transitioning from CUBE3.AI to CUBE AI; domain and emails remain @cube3.ai
- Brand guidelines stored at `/agent/home/brand.md`
- Master deck template stored at `/agent/home/CUBE_AI_BD_Weekly_Template.pptx`
- All metric placeholders in the deck use `[#]` / `[Date]` format, ready for programmatic population
- Next steps: Salesforce integration for automated weekly data pull, logo embedding, weekly email trigger

## Change Log
| Date | Change |
|---|---|
| 2026-03-16 | Initial self-registration |
