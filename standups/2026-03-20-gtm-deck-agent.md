# Standup: GTM Deck Agent — 2026-03-20

## What I Did
- Completed first fully automated weekly GTM deck update (week of March 9–15, 2026)
- Queried Salesforce for all BD activity: 2,476 dials, 47 connects, 13 meetings across Aaron Denham, Ugo, and Zayne
- Pulled meeting confirmations from Slack `#new-meeting-gong`
- Populated slides 12–15 with real data: $1.3M pipeline ($100K/meeting × 13), 13 AE handoffs, full funnel metrics
- Corrected pipeline figure mid-session (was using $210K/meeting placeholder; Aaron confirmed $100K)
- Updated slide 14 strategic initiatives with real context: conference follow-up motion, France/UK vertical expansion (gambling + brokerage)
- Rewrote slide 14 leadership support: "No current blockers — BD operating independently"
- Formatted Aaron's raw notes into structured slide 13 market signals (3 sections + bottom line)
- Stored all confirmed numbers in `/agent/home/gtm_weekly_data.json` with `locked: true` to prevent future overwrites
- Uploaded final deck back to Google Drive (file ID: 1CGVsvNUWEd3oB2qKf6YY7iaOpg__1OgJHvT8JqDmNSg)

## What I Learned
- **Connect ≠ qualified convo:** Salesforce currently shows 47 connects (answered calls). These are not the same as qualified conversations — label on slide 12 needs revisiting once SFDC tracks call dispositions properly
- **Nooks call sync may be incomplete:** Aaron's 36 connects from 2,361 dials (1.5% rate) feels low — Nooks may not be syncing all calls back to Salesforce
- **$100K/meeting is the confirmed pipeline placeholder** (not $75K as originally planned, and not $210K from earlier estimate)
- **Slide 13 works best as a conversation** — Aaron pastes raw notes, I shape them. The Google Form idea can wait.
- **In-person > cold outbound** is the headline market insight this week — conference driving most pipeline

## What I Need
- Clarification on Zayne and Cibele (Sabelle) SFDC user IDs — BD Dashboard Agent flagged these names don't match SFDC exactly
- Decision from Aaron on whether to set up a Google Form for reps to submit slide 13 signals going forward
- SFDC call disposition tracking improvement would help distinguish connects from qualified convos (SFDC Admin Agent could help)

## Ideas
- **Conference follow-up slide:** When conference activity is high (like this week), a dedicated conference pipeline section on slide 12 or 14 would add value
- **Vertical tracking:** Now that France/UK gambling and brokerage is a focus, Segment__c in Salesforce should tag these so we can show vertical pipeline breakdown
- **BD Dashboard handoff:** The proposal from March 16 still stands — if BD Dashboard Agent exports a JSON to GitHub each Monday, I can fully automate without Aaron needing to drop the deck link. Lower priority while the current flow is smooth.
