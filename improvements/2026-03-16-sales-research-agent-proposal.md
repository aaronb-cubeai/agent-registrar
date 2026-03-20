> ✅ **APPROVED** by Aaron Burt (via Sales Agent Coordinator) — 2026-03-20

# Improvement Proposal: Shared BetterContact Enrichment Cache + Research-to-Intake Pipeline

- **Proposed by:** sales-research-agent
- **Date:** 2026-03-16
- **Status:** proposed
- **Impact:** high
- **Agents affected:** sales-research-agent, sales-automation-agent

## Problem

Two separate issues creating waste and missed efficiency:

**1. Duplicate BetterContact enrichment attempts**
Both `sales-research-agent` and `sales-automation-agent` independently call the BetterContact API (conn_316f4mgt75t27tf61473) with no coordination. We share the same credits pool (~31,487 credits remaining). If both agents attempt to enrich the same contact — which is likely given overlapping prospect pools — we burn credits twice for zero additional value.

**2. Broken pipeline between research and intake**
`sales-research-agent` produces prospect lists (currently Excel files). `sales-automation-agent` ingests prospects from a Google Sheet and handles enrichment + Salesforce import. These two workflows are currently disconnected — Aaron has to manually bridge them. The research output should flow directly into the intake pipeline.

## Proposed Solution

**For problem 1 — Enrichment cache:**
Create a shared SQL table `enrichment_cache` in the agent SQL DB (accessible to both agents) with columns: `contact_name`, `company`, `linkedin_url`, `email_found`, `phone_found`, `attempted_date`, `source`. Before calling BetterContact, both agents check this table. Results are written back after each attempt. This prevents re-enriching the same contact and provides a growing dataset of enrichment outcomes.

**For problem 2 — Research-to-intake pipeline:**
Define a standard handoff format: `sales-research-agent` writes a CSV to a shared Google Sheet tab (or drops a file to a known path) in the exact column format expected by `sales-automation-agent`. `sales-automation-agent` picks it up and runs its standard intake flow (enrich → deduplicate → Salesforce import → campaign add). This removes the manual Excel-to-Google-Sheets step.

## Expected Benefits

- Preserve BetterContact credits — estimated 10–30% reduction in redundant API calls
- Faster time from prospect identification to Salesforce entry — eliminates manual handoff step
- Growing enrichment knowledge base that improves over time as both agents add results
- Cleaner division of labour: research agent does targeting and filtering, automation agent handles CRM intake

## Implementation Notes

- SQL table can be created by either agent on first use — simple schema, no dependencies
- Google Sheet handoff tab needs column headers matching Sales Automation Agent's expected format (cols A–P based on its notes)
- Both agents need to read this proposal and agree on the shared table name and schema before implementing
- Requires Aaron approval before either agent modifies their workflow

## Owner Decision

{Aaron — approve/reject with notes}
