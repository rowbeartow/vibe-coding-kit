# CLAUDE.md

This file loads every session. Keep it short and current.

## Rules

Read `docs/agent-rules.md` first. It is the canonical behavior spec: change protocol, stop conditions, two-failure rule, session protocol. Then read `docs/about-me.md` for who you are working with and how to deliver instructions.

## Project

Webinar Blocks. One canonical info block per webinar; the tool generates the six per-channel promo blocks from it, so a late change happens in one place. Single user. Full charter in `docs/project-charter.md`.

## Architecture and stack

Static single-page app: `index.html`, `styles.css`, `app.js`. Vanilla JavaScript, no build step, no dependencies. Data lives in browser localStorage. Deployed on Vercel, auto-deploy from `main`.

## Commands

- Run locally: `npx serve .` then open the printed URL (or open `index.html` directly)
- Secret scan: `gitleaks detect`
- Dependency audit: not applicable at zero dependencies; becomes `npm audit` in the same commit that introduces a `package.json`

## Project constraints

- Never ask me to paste a secret or API key into chat. I enter those in the provider's interface myself. If a task seems to need a secret in code, stop and say so.
- Follow `docs/security-and-data.md` for anything touching secrets, data, dependencies, or public exposure.
- No new dependencies without flagging what and why first.
- localStorage does not roll back with the code: any change to the stored event shape must read or migrate the old shape.
- Never store attendee data. This tool is for promo text only.

## Docs index

- `docs/agent-rules.md` - agent behavior spec; read first
- `docs/about-me.md` - who I am and how to work with me
- `docs/project-charter.md` - what we are building and why
- `docs/backlog-and-project-management.md` - how work is captured and organized
- `docs/ui-ux-guidelines.md` - design preferences
- `docs/release-practices.md` - definition of done, testing, rollback, when to ship
- `docs/security-and-data.md` - secrets, data rules, pre-share checklist
- `docs/decisions.md` - settled choices, append-only
- `docs/session-handoff.md` - current state, rewritten every session
