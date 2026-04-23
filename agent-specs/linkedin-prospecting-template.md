# LinkedIn Prospecting Agent — Gold Standard Template

> **Purpose:** Replace the 5 broken/semi-manual LinkedIn agents with one battle-tested template each rep can deploy.

## The Problem Today

Every rep is running their own LinkedIn agent with the same issues:
- Typos and grammatical errors in outreach messages
- Adding contacts outside the approved target list
- Everyone bolting on manual review as a workaround
- No standardized quality gates

## Agent Design

### Core Architecture

```
[Target List] → [Prospect Selection] → [Message Draft] → [Quality Gate] → [Human Approval Queue] → [Send]
```

**The human-approval step is BY DESIGN, not a workaround.** At this stage of AI reliability, outreach messages should be human-reviewed before sending. The goal is to reduce the rep's work from "research + write + send" to just "review + approve."

### Input: Target List (Strict Scope)

The agent MUST only prospect from an explicitly provided list. No autonomous list expansion.

**Accepted formats:**
- Salesforce report/list view (preferred — pull via SOQL)
- CSV upload with company name + LinkedIn URL
- Sales Navigator saved list (if SN integration available)

**Guardrail:** Before composing any message, the agent must verify the prospect belongs to the approved list. If not on the list → skip and log.

### Step 1: Prospect Research

For each contact on the list, gather:
- Current role, title, tenure
- Company recent news (last 90 days)
- Mutual connections or shared groups
- Recent LinkedIn activity (posts, comments, shares)
- Territory-specific context (regulatory news, fraud incidents — feed from Market Intelligence agent when available)

### Step 2: Message Composition

**Rules:**
1. Max 300 characters for connection requests, 500 for InMails
2. NO company pitch in first message — lead with relevance
3. Reference something specific: their post, company news, shared connection
4. One clear CTA (usually a question, not a meeting request)
5. Tone: professional but human, no corporate buzzwords
6. MUST spell-check and grammar-check before submission

**Personalization tiers:**
- **Tier 1 (High priority):** Fully custom message referencing specific activity
- **Tier 2 (Medium):** Semi-custom with company-specific hook
- **Tier 3 (Low):** Template with industry-specific variable fills

### Step 3: Quality Gate (Automated)

Before presenting to the rep, auto-check:
- [ ] Spell check passed
- [ ] Grammar check passed
- [ ] Prospect is on approved list
- [ ] Message under character limit
- [ ] No company pitch in first touch
- [ ] Personalization element present
- [ ] CTA present

**If any check fails → auto-revise and re-check (max 2 retries), then flag for manual review.**

### Step 4: Human Approval Queue

Present the rep with a daily batch (morning delivery, configurable time):
- Prospect name + title + company
- Draft message
- Personalization source (e.g., "Referenced their Jan 15 post about X")
- Quality gate score (all passed / flags)
- One-click: ✅ Approve | ✏️ Edit | ❌ Skip

**Target: 80%+ approve rate without edits.** If approve rate drops below 60%, agent needs prompt tuning.

### Step 5: Send & Log

- Send approved messages via LinkedIn
- Log to Salesforce as Activity (Task or custom object)
- Track: sent, accepted, replied, meeting booked

## Rep-Specific Configuration

Each rep customizes:

| Setting | Example |
|---|---|
| Target list source | SFDC report ID or CSV |
| Territory/vertical focus | Aaron D: verticals by region |
| Tone preference | Formal / conversational / bold |
| Delivery time | 8am local |
| Daily batch size | 10-20 prospects |
| Excluded companies | Current customers, competitors |

## Metrics to Track

- **Messages drafted per day**
- **Approve rate** (% approved without edit)
- **Edit rate** (% approved with edit — analyze edits to improve)
- **Skip rate** (% rejected — analyze why)
- **Accept rate** (connection requests accepted)
- **Reply rate**
- **Meeting conversion rate**

## Integration Points

- **Salesforce:** Pull target lists, log activities
- **Market Intelligence Agent:** Feed territory-relevant news into personalization
- **Territory Digest:** Sync with weekly digest for coordinated outreach
- **Bank Stat Sheet:** Reference data for data-driven hooks (Aaron D's request)

## Deployment Plan

1. Build the template with all quality gates
2. Test with Aaron Burt first (dog-food it)
3. Roll out to one rep at a time, tune per rep
4. Weekly quality review for first month
5. Stabilize, then reduce oversight

## What This Replaces

| Before | After |
|---|---|
| 5 separate broken agents | 1 template, 5 configured instances |
| Manual review as workaround | Human approval by design |
| Typos reaching prospects | Automated quality gates |
| Scope drift (wrong contacts) | Strict list enforcement |
| No activity logging | Auto-log to Salesforce |
