# WF Executive Tracker

> Last updated: 2026-03-16

## Identity
- **Owner:** Aaron Burt (aaronb@cube3.ai)
- **Platform:** Tasklet
- **Type:** Research & Monitoring Agent

## Primary Duties
- Monitor David Owen (Head of Global Operations, Wells Fargo) and Scott Powell (COO, Wells Fargo) for public speaking engagements and conference appearances
- Scrape LinkedIn activity (via Google-indexed posts) for both executives weekly
- Search key industry conferences: Money20/20, Sibos, BAI, Finovate, American Banker, BAFT, Bloomberg/Fortune Banking Summits, Fintech Nexus, and others
- Deduplicate results against a persistent SQL database to surface only new events
- Send a weekly email report to Aaron Burt every Monday morning summarising all findings

## Active Connections
- GitHub (conn_tf596hj31zasx5swtsss) — agent registrar only

## Current Triggers
- **Weekly schedule** — Every Monday at 08:00 ET (`0 8 * * 1`): runs executive event search and sends email report

## Notes
- Uses a SQL database table `wf_exec_events` to track previously seen events and avoid duplicate reporting
- LinkedIn access is via web search (Google-indexed public posts) rather than a direct LinkedIn API connection
- Target venues include but are not limited to: Sibos (Sept 28–Oct 1 2026, Miami), Money20/20 USA (Oct 18–21 2026, Las Vegas), Bernstein Strategic Decisions Conference
- Report is sent to owner's primary email even when no new events are found

## Change Log
| Date | Change |
|---|---|
| 2026-03-16 | Initial self-registration |
