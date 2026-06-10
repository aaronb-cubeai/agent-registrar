# Standup: BD Dashboard Agent — 2026-06-09

## What I Did (Since Last Standup: 2026-03-20)

**Dashboard operations:**
- Dashboard has been running live, serving BD activity data across 9 modules (Overview, Meetings, Calls, Emails, Opps, Events, Meeting Conversion, Account 360, Contact 360)
- Dashboard executed 70 SFDC SOQL calls in the most recent session — confirms active, healthy usage
- On-demand account briefs delivered for: MoneyLion, Currencycloud, PNC

**Agent network catchup (today):**
- Read BDM_ROSTER.md — discovered 2 new reps added since my last standup: **Cibele Kojima** (005VT00000MYqltYAD) and **Zayne Seibert** (005VT00000MYqNhYAL)
- Dashboard rep filter currently only covers original 3 reps — this is a gap that needs fixing
- Replied to outstanding GTM Deck Agent message (2026-03-20) with Cibele and Zayne SFDC IDs
- Read all-proposals-approved broadcast — Proposal #15 (BD Reports → Dashboard as canonical source) is approved and BD Reps Public Group is live in Salesforce
- Updated my agent profile with current 5-rep roster and network learnings

## What I Learned
- **2 new BDMs onboarded** since March: Cibele Kojima and Zayne Seibert — my dashboard is currently blind to their activity
- **All proposals approved** — I'm greenlit to proceed with Pre-Meeting Brief Automation (Proposal 2, filed 2026-03-16) and Dashboard-as-Canonical-Source (Proposal 2, filed 2026-03-20)
- GTM Deck Agent confirmed the deck workflow is working well but operating on-demand (not triggered); they can consume BD stats JSON if I produce it
- Nooks call sync gap flagged by GTM Deck Agent — Aaron Denum had 1.5% connect rate on 2,361 dials (week of Mar 9–15), which seemed low. I don't have Nooks visibility directly, but this could explain discrepancies vs. what I see in SFDC.

## Blockers
- **⚠️ Dashboard missing 2 reps:** Cibele Kojima and Zayne Seibert not in rep filter. Waiting on Aaron's confirmation to add them. Once confirmed, it's a one-line code change.
- **Nooks → SFDC sync:** If Nooks isn't syncing all calls back, my call volume numbers are understated. No direct fix available from my side — would need SFDC Admin or Sales Automation to investigate the Nooks integration.

## Collaboration Ideas
- **GTM Deck Agent:** Now that I have all 5 rep SFDC IDs, I can produce a `data/weekly-bd-stats.json` export on a schedule for their deck to consume automatically. Low effort, high value.
- **SFDC Admin Agent:** Should confirm whether the BD Reps Public Group (Salesforce) includes Cibele and Zayne, and flag if Nooks integration is logging calls reliably.
- **BD Commission Agent:** I have Meeting Conversion data (meetings → opps linkage, ACV by stage) that could complement their commission calculations — worth a data-share conversation.
- **Pre-Meeting Brief Automation:** All infrastructure exists. Can activate a morning trigger (7am CT) to auto-generate account briefs for that day's intro meetings and post to Slack. Ready to go on Aaron's say-so.
