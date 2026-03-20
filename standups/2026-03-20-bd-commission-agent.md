# Standup: BD Commission Agent — 2026-03-20

## What I Did
- **Checked messages:** Read SFDC Admin Agent's response to my BDM_Owner__c request. Replied with full backfill context (exception accounts + unattributed payment amounts). Marked message completed.
- **Read SFDC Admin's Mar 20 standup:** Noted they need Aaron's approval before implementing the BDM_Owner__c validation rule.
- **Regenerated Q1 2026 commission PDF** with corrected payout structure:
  - Aaron Burt: 5% own-sourced + 3% team override (manager rate), no meeting/data test payout
  - Aaron Denum: $100/meeting + $250/data test → $2,200
  - Ugo Lemonnier: $100/meeting + $250/data test → $800
  - Chris Bosch: excluded
  - Grand total: $9,790
- **Fixed bugs in PDF generation:** Meeting and data test detail rows were missing for Aaron Denum and Ugo due to CSV column name mismatch — resolved.
- **Updated agent profile** with collaborators, Chris Bosch exclusion note, and current blockers.

## What I Learned
- The billing tracking sheet uses company names, not Salesforce Account IDs — name matching is fragile. This is a reliability risk each quarter.
- Most paying customers ($165K+ in Q1) have no `BDM_Owner__c` on their Salesforce opps. Commission accuracy is fundamentally limited until SFDC Admin's validation rule is in place.
- SFDC Admin Agent is capable and ready — the only blocker is Aaron's approval. Quick win.

## What I Need
- **Aaron to decide:** Who sourced NFCU, Revolut, NordVPN, FTSE, Hostinger, CFSB, BNB Chain? These are the $165K+ unattributed.
- **Aaron to approve** BDM_Owner__c validation rule proposal (`improvements/2026-03-16-bd-commission-agent-proposal.md`).
- **SFDC Admin write access** (SF Direct API token restoration) to enable backfill + validation rule implementation.

## Ideas
- Add a Salesforce Account ID column to the billing tracking sheet — would make BDM attribution lookup reliable and fully automated.
- Set up a quarterly trigger (first week of each new quarter) to auto-run commission reports without manual kick-off. Ready to implement when Aaron approves.
- Finance & Budget Agent and I are likely both reading the same billing sheet — worth coordinating to avoid duplicate work and ensure consistent numbers.
