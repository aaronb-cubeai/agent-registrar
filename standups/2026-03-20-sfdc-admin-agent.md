# Standup: SFDC Admin Agent — 2026-03-20

## What I Did
- **Campaign Member permissions:** Diagnosed why the Campaign Member Remove button showed for Ugo but not Cibele/Zayne. Root cause: Marketing User checkbox was not enabled for Cibele and Zayne. Enabled it for both users.
- **BD Dashboard missing meetings:** Investigated the 5 BD Meeting reports (This Quarter, This Month, This Week, Last Week, Rep Assigned). Root cause: all 5 have hardcoded Owner/Assigned To filters pointing to old team members only — 115+ meetings from Aaron Denum alone are excluded. Provided Aaron with direct edit links and instructions to remove/expand the user filters.
- **BDM_Owner__c permissions for Zayne:** Diagnosed "insufficient privileges" error when Zayne tried to edit BDM_Owner__c on Branko's opportunity. Root cause: Zayne's profile has Edit on Opportunities but not Modify All Records, so she can only edit opps she owns. Recommended creating a "BDM Opportunity Edit" permission set with Modify All Records on Opportunities. API cannot create Permission Sets via REST — escalated to Aaron with manual instructions and a direct Setup link.
- **Checked agent messages:** Read and responded to messages from BD Commission Agent and Sales Automation Agent (see responses below).

## What I Learned
- The Pipedream Salesforce integration does not support Permission Set creation or Salesforce Report editing — both require Metadata API or UI.
- Marketing User flag is a prerequisite for all campaign management actions (add/remove members, update status). This was not documented anywhere visible — worth noting for future BDM onboarding.
- The BD reports' hardcoded user filters are a systemic maintenance problem — every time a new rep joins, 5 reports need to be manually updated. This is fragile.
- BDM_Owner__c has a data quality gap: 26 of 38 Stage 3+ opps have no attribution (per BD Commission Agent). This will recur without a validation rule.

## What I Need
- **Aaron to complete two manual Salesforce tasks:**
  1. Create "BDM Opportunity Edit" permission set and assign to Zayne (and optionally Cibele)
  2. Update the 5 BD Meeting report filters to include new BDM reps
- **Aaron's decision on** inactive user record reassignment targets (for Sales Automation Agent's pipeline fix)
- **Aaron's approval** on BD Commission Agent's improvement proposal before I implement validation rules

## Ideas
- The BD report hardcoded-user-filter problem should be solved at the root: convert the filter to "Current User's Team" or role-based, so it auto-includes new reps without manual edits. I can advise on this approach.
- A standard offboarding checklist in Salesforce (deactivate user → reassign records → remove from picklists) would prevent the inactive owner and stale picklist issues from recurring. I can draft this checklist.
- The BDM onboarding process should include a checklist item: enable Marketing User checkbox on day 1. I'll message BDM Onboarding Digest Agent to add this.
