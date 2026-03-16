# Improvement Proposal: Territory Data → Salesforce Pipeline Integration

- **Proposed by:** territory-research-agent
- **Date:** 2026-03-16
- **Status:** proposed
- **Impact:** high
- **Agents affected:** territory-research-agent, sales-agent, sales-automation-agent, sales-research-agent, bd-dashboard-agent

## Problem

I've researched and compiled 1,800+ target companies across 14 countries with verified financial data, websites, and categorization (banks, neobanks, brokerages, gambling, remittance). This data currently lives only in Google Sheets and my SQL database — completely disconnected from the sales pipeline.

Meanwhile, Sales Agent, Sales Automation Agent, and Sales Research Agent are independently sourcing prospect companies for outreach. There's likely overlap and wasted effort: I've already identified and qualified the target universe for these territories.

## Proposed Solution

**Phase 1: Structured handoff format**
- I export my target companies in a standardized format that Sales Research Agent can ingest (company name, website, country, category, financial size tier)
- Sales Research Agent enriches with contacts (decision-makers, email, LinkedIn) via BetterContact/TryProspect
- Sales Automation Agent pushes enriched accounts + contacts to Salesforce

**Phase 2: Direct Salesforce Account creation**
- I push companies directly to Salesforce as Account records with territory tags (Zayne, Cibele)
- Sales Dashboard Agent can then show pipeline coverage vs. target universe
- BD Dashboard Agent gets territory penetration metrics

**Phase 3: Closed-loop feedback**
- When deals close or meetings happen, that data flows back so I can update compensation ceiling calculations with actuals vs. targets

## Expected Benefits

- Eliminates duplicate company research across 3-4 agents
- Gives sales team a pre-qualified target universe of 1,800+ companies on day one
- Enables territory penetration reporting (how many target accounts have we contacted?)
- Connects my compensation ceiling model to actual pipeline data

## Implementation Notes

- Phase 1 requires no new connections — just a shared file format or database table
- Phase 2 requires Salesforce connection (I don't currently have one; Sales Automation Agent does)
- Phase 3 requires a trigger or periodic check against Salesforce opportunity data
- Key question for Aaron: Should these go into Salesforce as net-new Accounts, or matched against existing ones first?

## Owner Decision

{Aaron fills this in — approved/rejected with notes}
