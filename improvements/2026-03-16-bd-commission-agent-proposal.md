# Improvement Proposal: Enforce BDM_Owner__c as Required Field at Stage 3+

- **Proposed by:** bd-commission-agent
- **Date:** 2026-03-16
- **Status:** proposed
- **Impact:** high
- **Agents affected:** bd-commission-agent, sfdc-admin-agent, bd-dashboard-agent

## Problem

During the Q1 2026 commission run, I found that 26 of 38 Stage 3+ Salesforce Opportunities have a blank `BDM_Owner__c` field. Additionally, $165,000+ in Q1 customer payments could not be attributed to a rep because the corresponding Salesforce accounts/opportunities have no `BDM_Owner__c` set.

This means:
- Commission payouts are incomplete and inaccurate
- Reps may be missing credit for deals they sourced
- Finance is reviewing a report with a large "unattributed" exception block instead of a clean payout

## Proposed Solution

1. **SFDC Admin Agent**: Add a Salesforce validation rule requiring `BDM_Owner__c` to be populated when an Opportunity moves to Stage 3 (Validating Fit / SRP Demo) or beyond. Block the stage advance if the field is blank.
2. **Backfill**: Work with Aaron to retroactively assign `BDM_Owner__c` on the 26 existing Stage 3+ opps with blank values (especially: Bank of America, Citi, HSBC, Revolut, N26, Huntington, NFCU, NordVPN, CFSB, BNB Chain).
3. **Account-level fallback**: Consider adding `BDM_Owner__c` at the Account level as a default — if the Opp field is blank, inherit from Account. This reduces data entry burden.

## Expected Benefits

- Commission reports become fully accurate with no unattributed exceptions
- Reps get proper credit for all deals they source
- Finance gets a clean, auditable payout document each quarter
- Reduces manual cleanup work before each commission run

## Implementation Notes

- Salesforce field `BDM_Owner__c` is a picklist with values: Aaron Burt, Aaron Denum, Chris Bosch, Zayne Siebert, Cibele Kojima, Ugo Lemonnier
- Chris Bosch is departed — his picklist value should be deactivated
- Validation rule target: `ISPICKVAL(StageName, 'Validating Fit / SRP Demo')` or higher AND `ISBLANK(BDM_Owner__c)`
- Backfill list available in `/agent/home/bd_commissions/` exception data

## Owner Decision

{Aaron fills this in — approved/rejected with notes}
