# Follow-Up Agent

> **Origin:** Aaron Denum's idea — "Being able to stay on top of all the email follow ups could help land a couple extra meetings per week/month"
> **Impact:** Direct pipeline impact — turns forgotten threads into booked meetings

## The Problem

Reps send outreach emails and then lose track. Follow-ups slip through the cracks because:
- High volume of simultaneous conversations
- No systematic tracking of "who needs a follow-up and when"
- Manual CRM task creation is tedious and inconsistent
- By the time they remember, the window has closed

## What This Agent Does

Monitors email activity in Salesforce, identifies conversations that need follow-up, drafts contextual follow-up messages, and delivers a daily action list.

## Core Logic

### What Triggers a Follow-Up?

| Scenario | Wait Period | Priority |
|---|---|---|
| Sent email, no reply | 3 business days | 🔴 High |
| Prospect opened but didn't reply | 2 business days | 🔴 High |
| Prospect replied, rep hasn't responded | 1 business day | 🔴 Urgent |
| Meeting scheduled, no confirmation | 1 business day before | 🟡 Medium |
| Proposal sent, no response | 5 business days | 🔴 High |
| Post-meeting, no next steps sent | 1 business day | 🟡 Medium |
| Cold outreach sequence — touch 2 | 4 business days after touch 1 | 🟡 Medium |
| Cold outreach sequence — touch 3 | 5 business days after touch 2 | 🟢 Low |
| Re-engagement (went dark 30+ days) | 30 days | 🟢 Low |

### Follow-Up Message Rules

1. **Never repeat the same message** — each follow-up must add new value
2. **Escalating value pattern:**
   - Touch 2: Add a relevant insight, case study, or data point
   - Touch 3: Different angle — reference a trigger event or mutual connection
   - Touch 4: Breakup email — last attempt, make it easy to say no
3. **Keep it short** — follow-ups should be 2-4 sentences max
4. **Reference the original context** — "Following up on my note about X"
5. **Clear CTA** — each follow-up has one specific ask

### Value-Add Library

The agent maintains a rotating library of follow-up value-adds:
- Relevant case studies by vertical
- Industry stats and benchmarks
- Recent news about the prospect's company (from Market Intelligence agent)
- New product features or announcements
- Relevant regulatory changes

## Daily Output: Follow-Up Action List

**Delivery:** Every morning, configurable time per rep

```
📬 FOLLOW-UP QUEUE — [Date]
━━━━━━━━━━━━━━━━━━━━━━━━━━━

🔴 URGENT (respond today)
1. [Contact Name] @ [Company] — They replied yesterday, you haven't responded
   Last message: "Thanks, can you send pricing?"
   → Draft: [pre-written response]

🔴 HIGH PRIORITY (3+ days waiting)  
2. [Contact Name] @ [Company] — Sent proposal 5 days ago, no response
   → Draft: "Hi [Name], wanted to check if you had a chance to review..."
   → Value-add: Attached similar case study for [their vertical]

3. [Contact Name] @ [Company] — Initial outreach, no reply (4 days)
   → Draft: "Hi [Name], saw [Company] just [news event]..."

🟡 MEDIUM
4-8. [Additional follow-ups...]

━━━━━━━━━━━━━━━━━━━━━━━━━━━
Summary: 3 urgent | 5 high | 4 medium | 2 low
Estimated time: 20 minutes to clear queue
```

### Rep Actions

For each follow-up:
- ✅ **Send** — approve and send the draft as-is
- ✏️ **Edit & Send** — modify then send
- ⏰ **Snooze** — push to tomorrow / next week / custom date
- ❌ **Skip** — mark as not needed (agent learns from skips)
- 🏁 **Close** — prospect responded elsewhere / deal moved forward

## Data Sources

| Source | What It Provides |
|---|---|
| Salesforce Activities | Email send/receive timestamps, task records |
| Salesforce Opportunities | Deal stage context for follow-up tone |
| Email tracking (if available) | Open/click data for prioritization |
| Market Intelligence Agent | News hooks for value-add follow-ups |
| Calendar | Meeting confirmations, no-shows |

## Salesforce Integration

### Read (SOQL queries):
- `Task` — email activities, follow-up tasks
- `Event` — scheduled meetings
- `Opportunity` — deal context
- `Contact` / `Lead` — prospect info
- `EmailMessage` — if Email-to-Salesforce enabled

### Write:
- Create follow-up `Task` records when follow-ups are sent
- Update `Task` status when completed
- Log follow-up activity for reporting

## Rep Configuration

| Setting | Default | Customizable |
|---|---|---|
| Follow-up wait periods | As above | Yes, per rep |
| Daily delivery time | 8:00 AM local | Yes |
| Max follow-ups per day | 15 | Yes |
| Auto-send (no approval) | OFF | Rep can enable for low-priority |
| Breakup email after touch # | 4 | Yes |
| Re-engagement threshold | 30 days | Yes |

## Success Metrics

- **Follow-ups sent per day** (target: 10-15 per rep)
- **Reply rate on follow-ups** (benchmark: 15-25%)
- **Meetings booked from follow-ups** (the money metric)
- **Queue clearance rate** — % of daily queue acted on
- **Time-to-follow-up** — how fast reps act after notification

## Build Plan

1. Start with SFDC Activity data — identify overdue follow-ups
2. Build the daily digest output (email format)
3. Deploy to Aaron Denum first (his idea)
4. Add draft generation in week 2
5. Add Market Intelligence integration in week 3
6. Roll out to remaining reps in week 4

## Dependency

- **Salesforce connection** (active on Sales Agent ✅)
- **Email integration** (for send capability — may need new connection)
- **Market Intelligence Agent** (for value-add hooks — build in parallel)
