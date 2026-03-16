# Improvement Proposal: Departed User Cleanup Protocol

- **Proposed by:** sfdc-admin-agent
- **Date:** 2026-03-16
- **Status:** proposed
- **Impact:** high
- **Agents affected:** sfdc-admin-agent, bd-commission-agent

## Problem

Chris Bosch has departed from Cube3.ai but remains present in Salesforce in multiple ways:
1. His user account may still be active in SFDC
2. His name remains as an active picklist value in `BDM_Owner__c` on Opportunities
3. Any open Opportunities or Campaigns still assigned to him have no active owner

This creates two risks:
- **Commission accuracy**: BD Commission Agent already excludes him from payouts manually, but his name appearing as a picklist option means sales reps could accidentally select him on new deals, creating attribution black holes
- **Security**: An inactive employee with an active SFDC user account is a security gap

The same problem will recur every time a team member departs without a formal offboarding checklist.

## Proposed Solution

1. **Immediate (one-time)**: Deactivate Chris Bosch's SFDC user account and deactivate/remove his `BDM_Owner__c` picklist value
2. **Ongoing (process)**: Establish a lightweight offboarding checklist that I run whenever Aaron signals a team member has departed:
   - Deactivate SFDC user
   - Remove from all active picklist values
   - Reassign open Opportunities/Campaigns to a named owner
   - Notify BD Commission Agent and Finance Agent to update any reports

## Expected Benefits

- Eliminates accidental attribution to departed reps
- Closes potential security gap from orphaned user accounts
- BD Commission Agent's commission runs require no manual exclusion logic
- Creates a repeatable, auditable process — no more ad-hoc cleanup

## Implementation Notes

- Requires SF Direct API write access (PATCH on User record + update Picklist metadata)
- Picklist metadata changes require Tooling API or Metadata API — may need a separate approach
- For immediate fix: deactivating the User record is a REST PATCH; picklist value deactivation requires Metadata API deployment
- I can handle the user deactivation immediately once SF Direct API is reconnected; picklist change may need to be done via Setup UI

## Owner Decision

{Aaron fills this in — approved/rejected with notes}
