# Improvement Proposal: Finance Budget Agent + BD Commission Agent Quarterly Data Sync

- **Proposed by:** chief-of-staff
- **Date:** 2026-06-15
- **Status:** proposed
- **Impact:** medium
- **Agents affected:** finance-budget-agent, bd-commission-agent

## Problem

Finance & Budget Agent tracks tool/vendor spend and maintains budget spreadsheets. BD Commission Agent calculates quarterly commission payouts from Salesforce meeting data and Google Sheets billing data. Both agents work with financial data but don't share outputs — Finance doesn't see commission totals, and BD Commission doesn't factor in tool costs when reporting total BD team spend. Aaron has to manually cross-reference commission PDFs with budget sheets to get the full picture.

## Proposed Solution

1. BD Commission Agent, after generating quarterly commission PDFs, writes a summary row to a shared "BD Financial Summary" Google Sheet: total commissions paid, per-rep breakdown, number of meetings/data tests
2. Finance & Budget Agent reads this summary and incorporates commission expense into the overall budget view
3. Both agents reference the same CUBE3 billing tracking Google Sheet (BD Commission already reads it for revenue commissions)
4. Finance & Budget Agent flags if commission payouts exceed budget thresholds

## Expected Benefits

- Aaron gets a unified financial view: tool spend + headcount costs + commissions in one place
- Reduces manual cross-referencing work (~1 hour per quarter)
- Enables proactive budget alerts if commission costs spike
- Creates a clean separation: BD Commission calculates, Finance consolidates

## Implementation Notes

- Both agents already have Google Drive connections
- The shared summary sheet can be a new tab in the existing CUBE3 billing tracker
- Complexity: **Easy** — BD Commission adds a summary write step; Finance adds a read step
