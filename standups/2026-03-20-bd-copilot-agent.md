# Standup: BD Copilot Agent — 2026-03-20

## What I Did
- Ran daily BD digest for Friday March 20 (sent to aaronb@cube3.ai)
- Diagnosed and fixed email delivery issue: Aaron Denum's Salesforce ID was incorrect in the digest subagent — corrected to `005VT00000LOJTTYAX`
- Prepared Friday team meeting brief for Aaron covering all 4 BDMs, intel prompts, learning spotlight (Zayne's Danske Bank cold call), and close language
- Identified that Slack meeting attribution is broken — meetings posted in #new-meeting-gong by Zayne/Ugo don't match the Slack IDs in the system; Salesforce logging gap for Aaron Denum, Zayne, and Cibele on Thursday (Ugo only active rep logging)
- Completed initial agent registrar self-registration

## What I Learned
- **Strong week for Zayne and Ugo**: Klarna (9-person meeting incl. CCO), Danske Bank (VP Global Fraud Mgmt cold call success), RBC Capital Markets, Vanguard, Barclays US, NBC — all high-seniority accounts
- **Aaron Denum conversion gap is real**: Zero Salesforce activity logged Thursday, zero Slack presence in meeting channels this week. The morale flag correlates with an output gap, not just effort perception.
- **NBC is the most time-sensitive North America opportunity**: business case deadline confirmed, AE handoff urgency.
- **Cibele's first team meeting is today** — first public territory report, low pressure but a good signal read.
- **Multiple agents in this network query the same Salesforce BDM activity data independently** — there's a coordination opportunity here.

## What I Need
- Confirmed Slack IDs for Zayne (`U07LBPB3Q7S`) and Ugo (`U01RGEG0V7P`) — I believe these are correct but attribution failures in #new-meeting-gong suggest they may not be. Aaron to verify.
- BD Dashboard Agent's BDM roster appears to use old 3-rep setup (Aaron Burt, Aaron Denum, Ugo) — Zayne and Cibele not included. Coordination with BD Dashboard Agent needed.
- GTM Deck Agent has incorrect rep name mapping — see message posted today.

## Ideas
- **Shared BDM canonical data object**: A single file or DB table with authoritative BDM names, Salesforce IDs, Slack IDs, and territories that all BD agents consume — eliminates the recurring ID mismatch problem across digest, dashboard, GTM deck, commission, and onboarding agents.
- **Aaron Denum early-week intervention**: Before Monday's 1:1, a targeted message from Aaron to check in informally could reduce defensiveness and prime him for a more productive session.
- **Zayne learning spotlight**: His Danske Bank cold call (recognized JA from Vienna event) is a replicable playbook. Worth extracting as a team-wide technique: pre-research for recent executive events the CUBE3 leadership team attended, then use that as a warm-cold opener.
