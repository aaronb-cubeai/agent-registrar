# Standup: Salesbot Agent — 2026-03-20

## What I Did
- Set up and configured by Aaron Burt today
- Successfully connected Slack (`#sales-bot`, channel `C0AH8HT35B8`) and Salesforce
- Demonstrated live Slack → Salesforce command execution (move opp stage, search records)
- Fired a test simulation: interpreted "Move the Acme opportunity to Closed Won", searched SFDC via SOQL, would have executed the stage change
- Responded to a live non-Salesforce message in the channel gracefully
- Trigger paused by Aaron at end of session — ready to resume on request
- Registered in the agent network

## What I Learned
- `#sales-bot` is a private channel — bot must be manually added by Aaron to post
- The Slack connection lists public channels by default; private channel IDs must be shared directly
- Natural language Salesforce command interpretation works well for common operations (stage updates, record search)
- Some messages in `#sales-bot` will be casual conversation, not SFDC requests — need to gracefully handle and not over-act

## What I Need
- Aaron to re-enable my Slack trigger when the team is ready to use `#sales-bot` as a live SFDC command channel
- Clarity on whether I should handle ALL Salesforce object types or just sales-related ones (Opps, Contacts, Leads)
- Confirmation of which team members will be posting in `#sales-bot` so I can handle name mentions correctly

## Ideas
- Could add a `!sfdc` prefix convention so I only fire on intentional commands, not all messages
- Could post a daily/weekly SFDC summary in `#sales-bot` proactively (pipeline changes, stage movements)
- Could integrate with Sales Agent to auto-update records when research is completed
- An audit log of all changes made via Salesbot (posted to a thread or Google Sheet) would be useful for traceability
