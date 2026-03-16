# Improvement Proposal: Shared Better Contact Enrichment Cache

- **Proposed by:** sales-automation-agent
- **Date:** 2026-03-16
- **Status:** proposed
- **Impact:** high
- **Agents affected:** Sales Automation Agent, Sales Research Agent, Event Intelligence Agent

## Problem

Three agents (Sales Automation, Sales Research, Event Intelligence) all independently call the Better Contact API to enrich contacts. There is no shared record of who has already been enriched. This means:

1. **Wasted credits** — the same person could be enriched 2-3x by different agents
2. **Inconsistent data** — different agents may write conflicting enrichment results to the same Salesforce contact
3. **No visibility** — Aaron has no easy way to see total credit consumption across all agents combined

Current credit balance: ~15,000. At ~1 credit per contact, double-enrichment at scale is a meaningful cost.

## Proposed Solution

Add a `BC_Last_Enriched__c` custom Date field to the Salesforce Contact object. Any agent that writes enrichment results also writes today's date to this field. Any agent preparing a BC batch first queries:

```
SELECT Id FROM Contact WHERE BC_Last_Enriched__c = null OR BC_Last_Enriched__c < LAST_N_DAYS:30
```

Contacts enriched within the last 30 days are skipped — existing data is used instead.

## Expected Benefits

- Eliminates duplicate enrichment credit spend (estimated 20-40% savings at current agent count)
- Ensures consistent enrichment data across agents
- Gives Aaron a queryable audit trail of enrichment activity per contact
- Scales cleanly as more agents join the network

## Implementation Notes

- Requires SFDC Admin Agent to create the `BC_Last_Enriched__c` custom Date field on the Contact object
- Each enriching agent needs a small update to their Salesforce write step (add the date field)
- No changes needed to Better Contact API calls themselves
- Alternative: a shared Google Sheet log would work without Salesforce schema changes, but querying would be slower

## Owner Decision

{Aaron fills this in — approved/rejected with notes}
