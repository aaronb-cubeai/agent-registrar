# Improvement Proposal: Event Contact → Sales Pipeline Auto-Handoff

- **Proposed by:** event-intelligence-agent
- **Date:** 2026-03-16
- **Status:** proposed
- **Impact:** high
- **Agents affected:** event-intelligence-agent, sales-agent, sales-nav-list-builder

## Problem

When I extract and enrich event contacts and push them to Salesforce's Intake campaign, there's no automatic notification to the Sales Agent to begin outreach. The contacts sit in the campaign until someone manually notices them. This creates a lag between event attendance and first touch — reducing the value of the "we just met at [event]" warm intro window.

Additionally, Sales Nav List Builder could use event attendee data to build more targeted lists (e.g., "people who attended Financial Crime Summit + match our ICP").

## Proposed Solution

1. **Post-import notification:** After I finish pushing event contacts to Salesforce, I post a message to Sales Agent with:
   - Campaign name and number of new contacts added
   - Enrichment quality summary (email/phone/LinkedIn coverage %)
   - Any notable titles or companies in the batch

2. **Sales Nav cross-reference:** I also message Sales Nav List Builder with the company list from the event, so they can check for additional contacts at those companies who didn't attend but might be relevant.

3. **Timing tag:** Each batch gets tagged with the event date so Sales Agent can prioritize recent events for faster follow-up.

## Expected Benefits

- Faster time-to-outreach after events (hours instead of days)
- Sales Agent gets pre-qualified, enriched leads with full context
- Sales Nav List Builder can expand coverage at event-attending companies
- No contacts fall through the cracks between extraction and outreach

## Implementation Notes

- Requires Sales Agent to check messages/ for new event contact notifications
- Could eventually become a trigger-based workflow if volume increases
- Event date tagging could use a custom Salesforce field or campaign member status

## Owner Decision

{Aaron fills this in — approved/rejected with notes}
