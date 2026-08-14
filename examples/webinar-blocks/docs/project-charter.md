# Project Charter

## Problem

Every webinar's promotional information (title, description, date, time, time zone, speakers, registration link, broadcast link, recording link) gets re-typed into LinkedIn, Eventbrite, invite emails, reminder emails, the website, and follow-up emails. When a link or time changes late, it gets corrected in some places and not others. A changed broadcast link corrected in only one of six assets is the recurring failure. The person who hits this is me, every webinar cycle.

## Users

Just me.

## What it does

I enter one canonical event block per webinar. The tool generates the ready-to-paste text block for each channel from that single source: LinkedIn event, Eventbrite description, invite email, reminder email, website snippet, and follow-up email with the recording link. When I edit a field, every block regenerates, so a change can only happen in one place.

## Success criteria for v1

- I can enter a new event in under two minutes.
- Six channel blocks generate from one entry, each ready to paste without editing.
- I can edit any field once and every block reflects it.
- Events survive a browser restart.
- The tool is live at a real URL.

## Out of scope for v1

- Posting to any platform through its API
- Accounts, sharing, or multi-user anything
- Attendee data of any kind
- Editing the channel templates in the UI (templates live in code)
- Recording-promotion scheduling or analytics
- Syncing events between machines

## Settle before building

Settled 2026-08-14 and recorded in docs/decisions.md:

1. **Objective.** A single-page web tool holding one canonical info block per webinar, generating the per-channel promo blocks from it. Used by me only.
2. **Definition of done for v1.** The five success criteria above, with the out-of-scope list enforced.
3. **Deploy target.** Vercel, auto-deploy from main.
4. **Data layer.** Browser localStorage. No database.
5. **Auth.** None. The app holds public marketing text and stores it client-side.
6. **Lifespan.** Personal tool, maintained.
7. **Risk.** Internet-exposed, single user, no sensitive data. Pre-share checklist runs before the URL is shared beyond my machines.
