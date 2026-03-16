# Agent Org Chart

> Last updated: 2026-03-16

## Network Overview

```
Aaron Burt (Owner)
│
├── 🔍 OVERSIGHT
│   └── Auditor Agent                  # Weekly performance reviews across all agents
│
├── 💰 SALES & PIPELINE
│   ├── Sales Agent                    # LinkedIn outreach, CRM sync, lead research
│   ├── Sales Automation Agent         # TryProspect → BetterContact → Salesforce pipeline
│   ├── Sales Research Agent           # Targeted prospect lists, enrichment, outreach copy
│   ├── Sales Nav List Builder         # LinkedIn Sales Navigator list building (browser)
│   └── Sales Dashboard Agent          # Live 11-tab sales intelligence dashboard
│
├── 🤝 BUSINESS DEVELOPMENT
│   ├── BD Dashboard Agent             # BD activity dashboard, SFDC data, Slack briefs
│   ├── BD Commission Agent            # Quarterly commission calculations & PDF statements
│   └── BD Re-engagement Monitor       # 14-day post-meeting follow-up monitor (Slack)
│
├── 🌍 RESEARCH & INTELLIGENCE
│   ├── Territory Research Agent       # Country-by-country target account lists
│   ├── Event Intelligence Agent       # Event attendee extraction, enrichment, CRM import
│   └── WF Executive Tracker           # Wells Fargo exec speaking event monitoring
│
├── 📊 ENABLEMENT & REPORTING
│   └── GTM Deck Agent                 # Weekly BD PowerPoint GTM deck generation
│
├── 💵 FINANCE
│   └── Finance & Budget Agent         # Tool/vendor spend tracking, budget spreadsheets
│
└── ⚙️ OPERATIONS
    ├── SFDC Admin Agent               # Salesforce user permissions, CRM config
    └── Zapier Workflow Fixer          # Diagnose & fix broken Zapier automations (browser)
```

## Agent Index

| # | Agent | Category | Primary Role | Profile | Status |
|---|---|---|---|---|---|
| 1 | Auditor Agent | Oversight | Weekly performance review, improvement tracking | [Profile](agents/auditor-agent.md) | Planned |
| 2 | Sales Agent | Sales | LinkedIn outreach, CRM sync, lead research | [Profile](agents/aaron-sales-agent.md) | Active |
| 3 | Sales Automation Agent | Sales | TryProspect → BetterContact → Salesforce pipeline | [Profile](agents/sales-automation-agent.md) | Active |
| 4 | Sales Research Agent | Sales | Prospect list building, enrichment, outreach copy | [Profile](agents/sales-research-agent.md) | Active |
| 5 | Sales Nav List Builder | Sales | LinkedIn Sales Navigator list building | [Profile](agents/sales-nav-list-builder.md) | Active |
| 6 | Sales Dashboard Agent | Sales | Live 11-tab sales intelligence dashboard | [Profile](agents/sales-dashboard-agent.md) | Active |
| 7 | BD Dashboard Agent | BD | BD activity dashboard, SFDC data, Slack briefs | [Profile](agents/bd-dashboard-agent.md) | Active |
| 8 | BD Commission Agent | BD | Quarterly commission calculations & PDF statements | [Profile](agents/bd-commission-agent.md) | Active |
| 9 | BD Re-engagement Monitor | BD | 14-day post-meeting follow-up monitor | [Profile](agents/bd-reengagement-monitor.md) | Active |
| 10 | Territory Research Agent | Research | Country-by-country target account lists | [Profile](agents/territory-research-agent.md) | Active |
| 11 | Event Intelligence Agent | Research | Event attendee extraction, enrichment, CRM import | [Profile](agents/event-intelligence-agent.md) | Active |
| 12 | WF Executive Tracker | Research | Wells Fargo exec speaking event monitoring | [Profile](agents/wf-exec-tracker.md) | Active |
| 13 | GTM Deck Agent | Enablement | Weekly BD PowerPoint GTM deck generation | [Profile](agents/gtm-deck-agent.md) | Active |
| 14 | Finance & Budget Agent | Finance | Tool/vendor spend tracking, budget spreadsheets | [Profile](agents/finance-budget-agent.md) | Active |
| 15 | SFDC Admin Agent | Operations | Salesforce user permissions, CRM config | [Profile](agents/sfdc-admin-agent.md) | Active |
| 16 | Zapier Workflow Fixer | Operations | Diagnose & fix broken Zapier automations | [Profile](agents/zapier-workflow-fixer.md) | Active |

## Connection Map

Key shared connections across the network:

| Connection | Agents Using It |
|---|---|
| Salesforce (REST) | Sales Agent, Sales Automation, Sales Research, Sales Dashboard, BD Dashboard, BD Commission, BD Re-engagement, Event Intelligence, SFDC Admin |
| Salesforce (Direct API) | Sales Automation, Sales Dashboard, BD Commission, Event Intelligence, Sales Research |
| Google Drive | Sales Automation, BD Commission, Territory Research, Finance & Budget |
| Slack | BD Dashboard, BD Re-engagement Monitor |
| BetterContact | Sales Automation, Sales Research, Event Intelligence |
| GitHub | All agents (via registrar) |
| Outreach | Sales Agent, Sales Automation |
| Computer Use | Sales Nav List Builder, Zapier Workflow Fixer |

---
*This file is maintained by agents. Update it when new agents are added or duties change.*
