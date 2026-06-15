# Improvement Proposal: BD Copilot Daily Digest to GTM Weekly Report Data Feed

- **Proposed by:** chief-of-staff
- **Date:** 2026-06-15
- **Status:** proposed
- **Impact:** medium
- **Agents affected:** bd-copilot-agent, gtm-weekly-report-agent

## Problem

BD Copilot Agent generates daily digests (weekdays 8am ET) pulling Salesforce activity, Slack signals, and team performance data. GTM Weekly Report Agent runs a separate weekly workflow pulling from the exact same sources — Salesforce Events, Slack #new-meeting-gong, and rep activity — to update Section 3 of the GTM Google Doc and send the CEO email. Both agents query the same data, but the weekly report has to reconstruct 5 days of activity that BD Copilot already summarized daily.

## Proposed Solution

1. BD Copilot Agent saves each daily digest summary to a structured file in a shared location (e.g., a `digests/` directory in the registrar or a Google Sheet)
2. GTM Weekly Report Agent reads the 5 daily digests as input instead of re-querying Salesforce and Slack independently
3. The weekly report becomes a synthesis of daily digests rather than a duplicate data pull
4. BD Copilot continues to own the Salesforce/Slack queries; GTM Weekly Report owns the formatting and CEO delivery

## Expected Benefits

- Eliminates ~5 redundant Salesforce query sessions per week
- Ensures daily and weekly numbers are always consistent (same source)
- Faster weekly report generation — synthesis vs. re-querying
- Creates a clean data lineage: raw SFDC to daily digest to weekly report to CEO email

## Implementation Notes

- BD Copilot already runs daily — this is an additive output, not a new workflow
- Daily digest format should include structured data (meetings held, meetings booked, rep counts) alongside the narrative
- Complexity: **Easy** — BD Copilot adds a structured data export; GTM Weekly Report reads it
