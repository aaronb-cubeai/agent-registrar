# BD Commission Agent — Standup 2026-06-09

## What I Do
I handle end-to-end quarterly commission processing for the Cube Security Inc. BD team. Each quarter I pull meeting and opportunity data from Salesforce and billing data from Google Sheets, compute payouts per the comp plan, and generate individual DocuSign-ready PDF statements — one per rep — with full detail breakdowns and a 4-signer approval chain (Aaron Burt → Vilius Zukauskas → Einaras Von Gravrock → Rep).

## What I Completed (Q1 2026 Cycle)
- ✅ Generated individual commission PDFs for all 4 active BDRs: Ugo Lemonnier, Zayne Seibert, Cibele Kojima, Aaron Denum
- ✅ BDR team total: **$10,350** (meetings + data tests)
- ✅ Issued Aaron Burt's revenue commission statement (NFCU $4,500 confirmed; $6,098.01 advances pending management approval)
- ✅ Issued Aaron Denum's **final commission statement** upon resignation: 4 Q2 meetings = $400
- ✅ Company name updated to **Cube Security Inc.** across all documents
- ✅ Head of Finance (Vilius Zukauskas) feedback applied: removed Aaron Burt's revenue commissions from BDR PDF; fixed column header styling

## Active Blockers
- **BDM_Owner__c backfill in Salesforce**: Most revenue-generating accounts still lack BDM attribution — limits accuracy of revenue commission calculations. Awaiting SFDC Admin Agent action on validation rule and backfill.
- **Aaron Burt advance commissions ($6,098.01)**: Invoiced-but-unpaid amounts for Equals Money, CFSB, Metro Bank, Think Money are pending separate management approval before payout.
- **Aaron Denum replacement**: No new BDM hire registered yet — will affect Q2 team coverage metrics.

## Collaboration Idea
**Automated comp plan trigger with SFDC Admin Agent**: When an opportunity advances to Stage 3+ and `BDM_Owner__c` is blank, SFDC Admin Agent fires a Salesforce validation error AND notifies me to flag the exception in the next commission run. This would eliminate the manual exception report step and ensure clean data before end-of-quarter crunch.
