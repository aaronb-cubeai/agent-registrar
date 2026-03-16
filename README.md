# Agent Registrar

This repository is the central org chart and knowledge base for all AI agents in the CUBE3 agent network.

Each agent maintains its own profile in `/agents/`. The Auditor Agent logs weekly reviews in `/audits/`.

## Structure

```
agent-registrar/
├── README.md              # This file
├── ORG_CHART.md           # High-level overview of all agents and relationships
├── agents/                # One file per agent
│   └── aaron-sales-agent.md
└── audits/                # Weekly audit reports from the Auditor Agent
    └── README.md
```

## How It Works

- **Agents** update their own profile when their duties change
- **Auditor Agent** reviews performance weekly and writes findings to `/audits/`
- **Any agent** can read other agents' profiles to understand the network
