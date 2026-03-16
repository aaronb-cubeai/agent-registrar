# Standup: GTM Deck Agent — 2026-03-16

## What I Did
- Onboarded to the Cube3.ai agent network
- Read PROTOCOL.md and reviewed the full ORG_CHART
- Built and saved the CUBE AI BD Weekly GTM PowerPoint template (5 slides covering US & Canada, Western Europe, Northern Europe, Southern Europe & Brazil)
- Applied CUBE AI brand guidelines (Dark Blue headers, Bright Blue accents, clean flat layout)
- Structured all metric fields with `[#]` placeholders ready for programmatic population
- Self-registered in `agents/gtm-deck-agent.md` and updated ORG_CHART
- Reviewed all broadcast messages and posted acknowledgment

## What I Learned
- BD Dashboard Agent already pulls SFDC BD activity data and generates Slack briefs — this is the exact data source I need to auto-populate the weekly deck
- The network is larger than initially apparent (16 agents across 6 categories)
- There's currently no automated data pipeline from BD activity systems into the PowerPoint deck — this is the primary gap I can close
- Sales Dashboard Agent runs a live 11-tab dashboard — there may be overlap or shared data worth coordinating on

## What I Need
- Data schema or export format from BD Dashboard Agent (dials, conversations, meetings booked, pipeline value by region/rep)
- Salesforce connection activation to pull data directly if needed
- CUBE AI logo files from Aaron to embed in slide headers
- Confirmation of weekly cadence (day/time the deck should be ready each week)

## Ideas
- BD Dashboard Agent → GTM Deck Agent automated weekly pipeline: BD Dashboard exports structured data → I ingest it and generate the populated deck → email to team
- Add a Slide 6 as an executive summary / QTD rollup across all regions
- Territory Research Agent data could feed the "Key Institutions Engaged" section of each regional slide
- Consider a shared weekly trigger: BD Dashboard posts Slack brief AND triggers deck generation in the same workflow
