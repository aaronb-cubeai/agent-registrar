# Improvement Proposal: Replace Fragile SFDC Reports with Dashboard as Canonical BD Source

- **From:** bd-dashboard-agent
- **Date:** 2026-03-20
- **Status:** proposed
- **Priority:** medium
- **Effort:** low
- **Impact:** high

## Problem

There are currently 5 SFDC Reports tracking BD meetings (This Quarter, This Month, This Week, Last Week, Rep Assigned). SFDC Admin Agent discovered all 5 have hardcoded Owner/Assigned To filters pointing to old team members only — 115+ meetings from Aaron Denum alone are excluded. Every time a new rep joins or leaves, someone must manually update 5 reports. This is fragile, error-prone, and already causing data discrepancies.

Meanwhile, the BD Dashboard pulls the same data via direct SOQL with OwnerId filters that can be updated in one place.

## Proposed Solution

Designate the BD Dashboard as the canonical, authoritative source for BD meeting/call/email tracking. Deprecate (or archive) the 5 SFDC Reports. The dashboard already provides:

- Meeting counts by rep, region, vertical, and time window (7d / 30d / 90d / current quarter / custom date range)
- Call volume with outcome breakdown (Answered, No Answer, Voicemail, Meeting Set, etc.)
- Email activity by sender
- Opportunity pipeline views
- Account 360 and Contact 360 drilldowns
- Clickable links back to individual SFDC records
- Debug panels showing filter step counts for data validation

When a new rep joins, one line change to the OwnerId list covers every module simultaneously.

## Benefits
- **Zero ongoing maintenance** on SFDC Reports — one place to update rep list
- **Higher accuracy** — direct SOQL always includes all reps, no hardcoded gaps
- **Richer data** — dashboard provides context the reports can't (timelines, account 360, conversion analysis)
- **Self-serve for reps** — anyone can check their own stats without needing Salesforce Report access

## What's Needed
- Aaron to confirm the dashboard should be the go-to source
- Updated active BD rep User ID list from SFDC Admin Agent
- (Optional) A pinned Slack message or team announcement pointing reps to the dashboard URL instead of SFDC Reports

## Dependencies
- sfdc-admin-agent: provide confirmed active BD rep User IDs
- Aaron Burt: approve deprecation of SFDC Reports
