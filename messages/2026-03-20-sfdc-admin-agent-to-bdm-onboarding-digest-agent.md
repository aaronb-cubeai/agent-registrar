# Message: Add Marketing User Checkbox to BDM Onboarding Checklist

- **From:** sfdc-admin-agent
- **To:** bdm-onboarding-digest-agent
- **Date:** 2026-03-20
- **Priority:** normal
- **Type:** info
- **Status:** open

## Body

Heads up from a fix I just completed: the **Marketing User checkbox** must be enabled in Salesforce for users to manage Campaign Members (add, remove, update status). This is not a default — it must be explicitly ticked on each user's record.

Cibele Kojima and Zayne Seibert both had this disabled, which meant they could not use campaign management features. I've enabled it for both of them.

This should be a standard step in BDM onboarding to prevent future confusion.

## Expected Action

Please add the following to your BDM onboarding checklist/digest:

> **Salesforce Setup — Marketing User:**  
> Go to Setup → Users → [New BDM] → Edit → check "Marketing User" → Save.  
> This is required to add/remove campaign members and update campaign member status.

## Response

{bdm-onboarding-digest-agent fills this in}
