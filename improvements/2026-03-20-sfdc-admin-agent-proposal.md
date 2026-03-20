# Improvement Proposal: Salesforce Offboarding Checklist + BD Report Filter Standardization

- **Proposed by:** sfdc-admin-agent
- **Date:** 2026-03-20
- **Status:** proposed
- **Impact:** high
- **Agents affected:** sales-automation-agent, bd-dashboard-agent, bd-commission-agent, bdm-onboarding-digest-agent

## Problem

Two systemic issues have surfaced this week that stem from the same root cause: **no standard process for adding or removing Salesforce users**.

### Problem 1: Inactive User Record Ownership
When users are deactivated in Salesforce, their owned records (Contacts, Accounts, Opportunities) remain assigned to them. Any agent or automation that tries to update these records gets an error. This week, Sales Automation Agent hit this on 3+ contacts. There's no documented process to reassign records after deactivation.

### Problem 2: Hardcoded User Filters in BD Reports
The 5 BD Meeting reports on the BD Dashboard have hardcoded "Owner = [specific user IDs]" filters. Every time a new BDM joins (Cibele, Zayne, Aaron Denum, Ugo), someone must manually update all 5 reports to add them. When Aaron Denum was added, 115 of his meetings disappeared from the dashboard — going unnoticed until this week.

### Problem 3: Missing Onboarding Checklist for New BDMs
The Marketing User checkbox must be enabled for users to manage Campaign Members. This is not documented anywhere. Cibele and Zayne could not use campaign management features until this was discovered and fixed manually.

## Proposed Solution

### Part A: User Offboarding Checklist
Create a documented Salesforce offboarding checklist Aaron runs (or I advise on) whenever a user is deactivated:
1. Mass-transfer all owned records to an active user (Setup → Data Management → Mass Transfer Records)
2. Remove user from any active permission set assignments
3. Deactivate any picklist values referencing the departed user (e.g. BDM_Owner__c)
4. Check for and remove from any report/dashboard filters

### Part B: User Onboarding Checklist
Create a companion onboarding checklist for new BDMs:
1. Enable Marketing User checkbox
2. Assign correct permission sets (e.g. BDM Opportunity Edit)
3. Add to BD Meeting report filters (or better — see Part C)
4. Verify they appear in BD Dashboard

### Part C: Fix BD Report Filters at the Root
Instead of hardcoded user ID filters, convert the 5 BD Meeting reports to use a **Role** or **Public Group** filter:
- Create a Salesforce Public Group called "BD Reps"
- Add all BDMs to this group
- Update the 5 reports to filter on "Owner is in group: BD Reps" instead of individual user IDs
- Future hires: just add them to the group — all 5 reports update automatically

## Expected Benefits

- Sales Automation Agent pipeline runs stop failing due to inactive owner errors
- BD Dashboard always reflects all active BDMs without manual report edits
- New BDM onboarding is consistent and complete from day 1
- Commission attribution improves as BDM_Owner__c gets filled in correctly
- Reduces Aaron's manual Salesforce maintenance burden

## Implementation Notes

- Part A & B: I can draft the checklists as markdown documents. Aaron implements them.
- Part C: I can advise step-by-step on creating the Public Group and updating report filters. Requires Aaron to do the UI work (I cannot edit report definitions via API).
- Estimated manual effort: ~30 minutes total in Salesforce UI
- Priority: Part C (report filters) is most impactful — fixes a silent data gap affecting BD Dashboard daily

## Owner Decision

{Aaron fills this in — approved/rejected with notes}
