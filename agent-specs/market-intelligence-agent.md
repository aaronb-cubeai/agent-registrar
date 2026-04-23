# Market Intelligence Agent

> **Origin:** Ugo Lemonnier's idea — "an agent updating us with news about ongoing scams, banks getting fined, prospects publicly talking about fraud and mules"
> **Impact:** Helps all 5 reps prioritize accounts based on real-world events

## The Problem

Reps are doing outreach without real-time awareness of what's happening in their territories. A bank that just got fined for AML failures is 10x more likely to take a meeting about fraud prevention — but reps don't find out until it's old news.

## What This Agent Does

Monitors public sources for fraud, financial crime, and regulatory news relevant to Cube3.ai's target accounts, then delivers actionable intelligence to reps organized by territory.

## Intelligence Categories

### 1. Scam & Fraud Incidents
- Crypto scams making national/regional news
- Pig butchering / romance scam busts
- Mule account networks exposed
- DeFi exploits and hacks

### 2. Regulatory Actions
- Banks fined for AML/KYC failures
- Regulatory enforcement actions (FinCEN, FCA, MAS, etc.)
- New compliance mandates or deadlines
- Consent orders / remediation requirements

### 3. Industry Signals
- Banks/FIs publicly discussing fraud prevention initiatives
- RFPs or vendor selections for fraud/compliance tools
- Earnings calls mentioning fraud losses
- Executive hires in compliance/fraud roles (new CMLRO, Head of Fraud, etc.)

### 4. Prospect-Specific Activity
- Target accounts in the news (any category)
- Leadership changes at target accounts
- M&A activity involving targets
- Partnership announcements (especially with competitors)

## Data Sources

| Source | Method | Frequency |
|---|---|---|
| Google News | Web search + scrape | 2x daily |
| Reuters, Bloomberg, Financial Times | RSS feeds | Real-time |
| Regulatory agency sites (FinCEN, FCA, MAS, AUSTRAC, etc.) | Web scrape | Daily |
| Chainalysis / Elliptic blogs | RSS | Daily |
| LinkedIn (company posts) | If integration available | Daily |
| CoinDesk / The Block / Decrypt | RSS | 2x daily |
| Territory-specific news sources | Web search by region | Daily |

## Output: Territory Intelligence Brief

**Delivery:** Daily digest (morning, configurable per rep) + real-time alerts for high-priority events

### Daily Digest Format

```
🔴 HIGH PRIORITY (act today)
━━━━━━━━━━━━━━━━━━━━━━━━
[Bank Name] fined $X by [Regulator] for [reason]
→ On your target list: YES | Territory: [region]
→ Suggested action: Reach out to [contact] referencing the fine
→ Opening line: "Saw the [regulator] action last week — curious how your team is thinking about [specific area]"

🟡 MONITOR (awareness)
━━━━━━━━━━━━━━━━━━━━━━━━
[Brief] — [Source] — [Date]

🟢 TERRITORY TRENDS (weekly roll-up)
━━━━━━━━━━━━━━━━━━━━━━━━
- [Region] seeing uptick in [type] enforcement
- [X] scam incidents reported in [country] this week
```

### Rep Routing

Each intelligence item is tagged to the relevant rep(s) based on territory assignment:

| Rep | Territory Focus |
|---|---|
| Aaron Burt | Strategic / enterprise |
| Aaron Denum | Regional verticals |
| Cibele Kojima | LATAM + specific verticals |
| Ugo Lemonnier | EMEA |
| Zayne Seibert | Assigned territory |

Use BDM Roster (GitHub: `BDM_ROSTER.md`) for territory mapping. Cross-reference target account lists in Salesforce.

## Integration Points

- **LinkedIn Prospecting Agent:** Feed relevant news into message personalization (Tier 1 hooks)
- **Territory Digest:** Merge intelligence into weekly digest (Zayne's request to link Monday digest to signals)
- **Salesforce:** Tag accounts with recent intelligence events for prioritization
- **Slack:** Post high-priority alerts to team channel

## Alert Thresholds

| Priority | Criteria | Delivery |
|---|---|---|
| 🔴 High | Target account directly involved, regulatory fine >$1M, competitor win/loss | Immediate Slack + email |
| 🟡 Medium | Industry trend, non-target company in territory, new regulation | Daily digest |
| 🟢 Low | General market news, distant geography | Weekly roll-up |

## Technical Approach

1. **Trigger:** Scheduled — run 2x daily (7am, 1pm per rep timezone)
2. **Sources:** Web search API + RSS feeds + targeted scraping
3. **Processing:** Classify each item by category, priority, territory, and target account match
4. **Dedup:** Track seen articles (by URL hash) to avoid repeat alerts
5. **Delivery:** Email digest + Slack alerts for high priority
6. **Storage:** Log all intelligence items to database for trend analysis

## Success Metrics

- **Meeting conversion lift:** Do accounts with recent intelligence convert to meetings at higher rate?
- **Time-to-outreach:** How fast do reps act on high-priority signals?
- **Rep satisfaction:** Is this actually useful or just noise?
- **Coverage:** % of target accounts with at least 1 intelligence event per month

## Build Plan

1. Start with Google News search + 3-4 RSS feeds (keep it simple)
2. Deploy to Ugo first (his idea, he's motivated)
3. Add sources incrementally based on signal quality
4. Tune priority thresholds based on rep feedback after 2 weeks
5. Integrate with LinkedIn agent once both are stable
