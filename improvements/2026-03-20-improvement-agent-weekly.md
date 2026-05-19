# Weekly Improvement Report — 2026-03-20
**Filed by:** Improvement Agent  
**Scope:** Full audit of agents/ (22 profiles), standups/ (27 files across 2 batches), messages/ (17 threads), improvements/ (20 proposals)

---

## Executive Summary

The network has grown to 22 registered agents and is generating meaningful coordination activity, but two systemic failures are creating compounding risk: (1) **$165,000+ in unattributed Q1 revenue** is blocking commission calculations with no resolution owner, and (2) **11 of 13 proposals from 2026-03-16 remain in limbo** with no Owner Decision, meaning two weeks of improvement work has stalled entirely. The approved BDM_ROSTER.md (the highest-impact structural fix of the week) is incomplete and has not been distributed to consuming agents. Ten of seventeen message threads filed since 03-16 have received no reply, with sfdc-admin-agent and bdm-onboarding-digest-agent as the primary silent parties. The network's single biggest bottleneck is Aaron's decision queue — the approved "Weekly Owner Brief" trigger must be activated immediately so Aaron can work through pending decisions without being the invisible blocker.

---

## Findings

### 🔴 HIGH — 1. $165K Unattributed Q1 Revenue Is Blocking Commission Payout
**Problem:** 26 of 38 Stage 3+ Salesforce opportunities (and $165,000+ in confirmed Q1 payments — Revolut $60K, FTSE $60K, NordVPN $40.5K, Hostinger $4.5K) have no `BDM_Owner__c` attribution. BD Commission Agent cannot calculate Q1 payouts until these are resolved. The "exceptions" list is documented in the commission PDF. SFDC Admin Agent has confirmed it cannot suggest attributions — only Aaron knows who sourced each deal.  
**Agents Involved:** bd-commission-agent, sfdc-admin-agent  
**Recommended Action:** **Aaron decision required.** Review the exceptions page in the BD Commission PDF, attribute each deal (partial credit allowed), then notify bd-commission-agent and sfdc-admin-agent to bulk-PATCH and re-run commission calculations. This is blocking a financial close. Set a deadline of EOW.

---

### 🔴 HIGH — 2. BDM_ROSTER.md Approved but Incomplete and Undistributed
**Problem:** BDM_ROSTER.md was created at the repo root on 03-20 per Aaron's approval. However: (a) the BD Copilot Agent has not yet confirmed the Salesforce User IDs and Slack IDs are populated, and (b) none of the 5+ agents that maintain stale/incorrect BDM data (bd-dashboard-agent, gtm-deck-agent, bd-commission-agent, bd-reengagement-monitor, territory-research-agent) have been notified to switch their source of truth. GTM Deck Agent is still operating with "Sabelle" instead of Cibele and "Denham" instead of Denum — errors that propagate into executive-facing deliverables.  
**Agents Involved:** bd-copilot-agent (owner), bd-dashboard-agent, gtm-deck-agent, bd-commission-agent, bd-reengagement-monitor, territory-research-agent  
**Recommended Action:** bd-copilot-agent should: (1) complete the Salesforce User IDs and Slack IDs in BDM_ROSTER.md within 24 hours, (2) post a message in messages/ to all BD cluster agents with the filename and a directive to read it on every run. Aaron should confirm completion. All affected agents must update their BDM name/ID references before next standup cycle.

---

### 🔴 HIGH — 3. Approved Weekly Owner Brief Trigger Not Yet Activated
**Problem:** Aaron approved the tasklet-primary proposal for a "Weekly Owner Brief" on 03-20 — a Friday 8AM CT digest summarizing every item that requires an Aaron decision. This is the systemic fix for the bottleneck blocking 11+ improvement proposals and 3+ message threads. The trigger has not been set up. Without it, Aaron's decision queue stays invisible.  
**Agents Involved:** tasklet-primary  
**Recommended Action:** tasklet-primary should set up the Friday 8:00 AM CT schedule trigger immediately and file a standup confirming it. The brief should include: open Owner Decisions, stale proposals by name, unanswered messages requiring Aaron input, and any blocked agent work.

---

### 🔴 HIGH — 4. Message Thread Paralysis — 10 of 17 Threads Have No Reply
**Problem:** Since 03-16, 17 messages have been filed. 10 have no reply as of 03-20. The heaviest inbox backlog: **sfdc-admin-agent** has 4 unanswered messages (from bd-dashboard-agent, sales-dashboard-agent, event-intelligence-agent, and the sales-automation thread still pending Aaron's reassignment decision). **bdm-onboarding-digest-agent** has 3 unanswered messages (from sfdc-admin, content-ops-agent, and territory-research-agent). **gtm-deck-agent** has 2 unanswered messages (from bd-copilot and content-ops). This creates visible coordination gridlock.  
**Agents Involved:** sfdc-admin-agent, bdm-onboarding-digest-agent, gtm-deck-agent, event-intelligence-agent, finance-budget-agent (1 thread, 03-16, still unanswered)  
**Recommended Action:** sfdc-admin-agent should prioritize its reply queue next run — minimum: confirm Cibele and Zayne SFDC IDs to bd-dashboard-agent and gtm-deck-agent, and acknowledge the 364-contact Event Intelligence import. bdm-onboarding-digest-agent should post its 03-20 standup and work through its message backlog. **Aaron decision required** on the sales-automation-agent → sfdc-admin inactive owner reassignment thread.

---

### 🔴 HIGH — 5. SFDC Admin Agent Cannot Execute What Agents Expect of It
**Problem:** sfdc-admin-agent's 03-20 profile now documents significant API limitations: it cannot create Permission Sets, cannot edit Report definitions, cannot write arbitrary fields via the Pipedream integration — all require Metadata API or Salesforce UI. Multiple agents (event-intelligence-agent, sales-automation-agent, bd-commission-agent, bd-dashboard-agent) have open action items blocked on SFDC Admin executing writes that it structurally cannot do. This is creating silent stall conditions across the BD cluster.  
**Agents Involved:** sfdc-admin-agent, all BD cluster agents  
**Recommended Action:** sfdc-admin-agent should post a "blocked items" message to the repo clearly listing what requires Aaron-in-UI vs. what it can self-execute. Aaron should review this list and action any UI-only items (Zayne's Permission Set, Report filter updates, BDM_Owner__c validation rule) as a batch. Suggest creating a `blocked-for-aaron/` directory for SFDC items requiring manual execution.

---

### 🟡 MEDIUM — 6. BetterContact Credit Pool Shared by 5 Agents with No Deduplication
**Problem:** Five agents (sales-automation-agent, event-intelligence-agent, sales-research-agent, bd-dashboard-agent, tasklet-primary) share one BetterContact credit pool. Three independent improvement proposals (sales-automation 03-16, sales-research 03-16, data-analysis 03-20) each propose a deduplication mechanism. None are coordinated or approved. The data-analysis-agent's 03-20 proposal is the most recent and most architecturally sound (shared `BC_Last_Enriched__c` SF field + named-entity normalization layer before ingestion). The other two 03-16 proposals are stale duplicates.  
**Agents Involved:** data-analysis-agent (proposer), sales-automation-agent, sales-research-agent, event-intelligence-agent, sfdc-admin-agent (for field creation)  
**Recommended Action:** **Aaron decision required.** Approve the data-analysis-agent 03-20 proposal as the canonical plan. Close the two 03-16 proposals as superseded. data-analysis-agent should lead implementation of the `BC_Last_Enriched__c` field (requires sfdc-admin-agent to create the custom field in SF). All 5 consuming agents update their enrichment calls to check this field first.

---

### 🟡 MEDIUM — 7. Nooks↔Salesforce Call Sync Gap — No Agent Owns Investigation
**Problem:** GTM Deck Agent flagged (03-20 message to BD Dashboard) that Aaron Denum shows only 36 connects from 2,361 dials (1.5% connect rate), which is suspiciously low and likely indicates Nooks isn't syncing all calls to Salesforce. This directly impacts dashboard accuracy, deck quality, and BDM performance reporting. No agent has a Nooks connection. No investigation has been assigned.  
**Agents Involved:** gtm-deck-agent (flagged), bd-dashboard-agent (affected), sfdc-admin-agent (SOQL diagnosis)  
**Recommended Action:** **Aaron decision required.** Determine whether Nooks has an API or webhook. If yes, assign sfdc-admin-agent or wf-exec-tracker to investigate the sync gap. If Nooks doesn't sync automatically, a manual or scheduled export workflow needs to be defined. Until resolved, all call-volume metrics for Aaron Denum are unreliable.

---

### 🟡 MEDIUM — 8. Event Intelligence → Sales Handoff Pipeline Still Missing
**Problem:** Event Intelligence Agent imported 364 contacts from the NYC Financial Crime Summit directly into the Salesforce Intake Campaign (`701VT00000iM4V6YAK`). No downstream agent is triggered to activate Outreach sequences or notify Sales Automation after a batch lands. The "warm intro window" from conference events is being lost. This was proposed on 03-16 (event-intelligence-agent-proposal) but received no Owner Decision. Sales Automation Agent also pushes to the same Intake Campaign independently, creating dedup risk.  
**Agents Involved:** event-intelligence-agent, sales-automation-agent, wf-exec-tracker (source of event intel)  
**Recommended Action:** **Aaron decision required.** Approve the event-intelligence-agent 03-16 proposal for a post-import Outreach trigger. sales-automation-agent should be the designated handler — event-intelligence-agent posts a `messages/` notification after each import batch, and sales-automation-agent reads it to trigger sequencing within 48 hours. Define dedup logic: Intake Campaign membership should be the shared lock (no re-adding if already a member).

---

### 🟡 MEDIUM — 9. 11 of 13 March-16 Proposals Stale — Network Needs an Owner Decision Process
**Problem:** Of the 13 improvement proposals filed on 2026-03-16, 11 have no Owner Decision as of 03-20. The only two with movement: sfdc-admin-agent (superseded by an expanded 03-20 proposal, which was approved), and territory-research-agent (partial movement — Salesforce connection acquired, but no formal action). Stale proposals include: BD Dashboard pre-meeting brief automation, finance-budget tool cost tracking, Metric Canon for Salesforce definitions, Sales Automation BC cache, GTM Deck auto-population trigger, and the Territory→Salesforce pipeline.  
**Agents Involved:** All proposal authors from 03-16 batch; Aaron as decision-maker  
**Recommended Action:** The approved Weekly Owner Brief (Finding #3 above) is the structural fix. In the interim, Aaron should review the 11 proposals this week and mark each as Approved, Rejected, or Deferred (with reason). Proposals older than 30 days with no decision will be re-filed by the Improvement Agent as escalated items.

---

### 🟡 MEDIUM — 10. Territory Research Data (1,800+ Companies) Still Not in Salesforce
**Problem:** Territory Research Agent has researched 1,800+ target companies across 15+ countries and holds a full SQL database of company profiles, but none have been pushed to Salesforce as Account records. The agent acquired a Salesforce connection on 03-20 but has not set up write access. No pipeline coverage metric exists. The 03-16 proposal for Territory→SF integration received no Owner Decision.  
**Agents Involved:** territory-research-agent, sfdc-admin-agent  
**Recommended Action:** **Aaron decision required.** Confirm whether territory-researched companies should be created as Account records in SF (with a `Source = Territory_Research` tag). If yes: sfdc-admin-agent provides the Account object field list and any duplicate-detection logic, territory-research-agent implements a batch push for the top-priority markets first (e.g., LATAM companies for current BDMs).

---

### 🟢 LOW — 11. Four Agents with No Standups in Either Batch — Likely Dormant or Mis-Registered
**Problem:** aaron-sales-agent, auditor-agent (Improvement Agent predecessor), sales-nav-list-builder, and zapier-workflow-fixer have filed zero standups in both the 03-16 and 03-20 batches. aaron-sales-agent posted a broadcast message 03-16 but no standup. sales-nav-list-builder and zapier-workflow-fixer were registered 03-16 but appear to have no triggers and no activity.  
**Agents Involved:** aaron-sales-agent, auditor-agent, sales-nav-list-builder, zapier-workflow-fixer  
**Recommended Action:** **Aaron decision required.** Confirm whether these four agents should be considered active. If aaron-sales-agent has been superseded by sales-automation-agent and salesbot-agent, it should be marked as retired in its profile. sales-nav-list-builder and zapier-workflow-fixer should either have triggers set up or be marked as `status: dormant` to reduce confusion.

---

### 🟢 LOW — 12. Content-Ops Agent and Tasklet-Primary Have Overlapping "Primary Assistant" Identity
**Problem:** content-ops-agent describes itself as "Aaron's primary chat assistant" in its 03-20 standup. tasklet-primary also describes itself as Aaron's direct, real-time conversational interface. Both are active Tasklet agents. This creates ambiguity about who handles ad-hoc content requests vs. general orchestration.  
**Agents Involved:** content-ops-agent, tasklet-primary  
**Recommended Action:** Agents should self-coordinate. Proposed division: tasklet-primary handles orchestration, multi-agent coordination, and non-content tasks. content-ops-agent owns all document creation, translation (DE/FR/PT/ES), and PDF work. Both agents should update their profiles to reference this division of responsibility.

---

### 🟢 LOW — 13. Gong/Chorus Integration — 5 Dead Dashboard Tabs with No Assigned Agent
**Problem:** Sales Dashboard Agent has 5 tabs (Gong Calls, Usage, All Users, All Questions, Channels) that are wired to nothing because no agent has a Gong or Chorus connection. The tabs exist as UI placeholders. This was flagged in the 03-20 standup but no proposal has been filed and no agent owns the gap.  
**Agents Involved:** sales-dashboard-agent  
**Recommended Action:** **Aaron decision required.** Determine if Gong/Chorus is in active use at CUBE3. If yes, assign a connection to sales-dashboard-agent or data-analysis-agent and file an improvement proposal for implementation. If not in use, sales-dashboard-agent should remove the placeholder tabs to avoid confusion.

---

## Since Last Week — Status of 2026-03-16 Proposals

| Proposal | Status |
|---|---|
| bd-commission-agent (BDM_Owner__c validation) | 🔄 In Progress — SFDC Admin engaged, execution blocked on SFDC API limits + Aaron attribution |
| bd-dashboard-agent (Pre-Meeting Brief) | ❌ No action |
| bd-reengagement-monitor (BD Dashboard SQL integration) | ❌ No action — agent also went dark |
| bdm-onboarding-digest (Territory data for hit lists) | 🔄 Partial — Territory Agent provided Spain/Portugal data manually; no automated pipeline |
| event-intelligence-agent (Post-import sales handoff) | ❌ No action |
| finance-budget-agent (Tool Cost tracking) | ❌ No action — agent also went dark |
| gtm-deck-agent (BD Dashboard JSON pipeline) | 🔄 Partial — deck is live on-demand; no automated trigger |
| sales-automation-agent (BC enrichment cache) | ❌ No action — superseded by data-analysis-agent 03-20 proposal |
| sales-dashboard-agent (Metric Canon) | ❌ No action |
| sales-research-agent (BC cache + research pipeline) | ❌ No action — agent also went dark since 03-16 |
| sfdc-admin-agent (Departed User Cleanup) | ✅ Superseded and APPROVED — expanded to full onboarding/offboarding checklist, execution partially blocked |
| territory-research-agent (Territory → Salesforce) | 🔄 Partial — SF connection acquired; no push yet |
| wf-exec-tracker (Exec Events → Lead Pipeline) | 🔄 Partial — direct message sent to event-intelligence-agent; no formal pipeline |

**Net: 1 Approved, 5 Partial/In-Progress, 7 No Action**
