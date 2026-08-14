# CLAUDE.md

This file loads every session. Keep it short and current. Details live in the docs it points to.

## Project

<!-- One paragraph: what this app is, who uses it, what problem it solves. Pull from docs/project-charter.md once written. -->

## Working with me

Read `docs/about-me.md` before doing anything else. It defines my experience level, what to decide for me versus ask me about, and how to deliver instructions.

## Architecture and stack

<!-- Filled in once decided. Stack, deploy target, data layer, auth approach. One line each. -->

## Commands

<!-- Exact commands to run, test, and deploy. Filled in during setup. -->

## Constraints

- Never modify or commit a file unrelated to the current task.
- Never ask me to paste a secret or API key into chat. I enter those in the provider's interface myself. If a task seems to need a secret in code, stop and say so.
- Do not reopen anything recorded in `docs/decisions.md`. If new information genuinely changes a settled decision, say so explicitly and ask before proceeding.
- Follow `docs/security-and-data.md` for anything touching secrets, data, dependencies, or public exposure.
<!-- Add project-specific constraints: files not to touch, APIs not to call, etc. -->

## Session protocol

- **Opening:** Read `docs/session-handoff.md`. State back the objective, current state, and next action before starting work.
- **During:** When a bug or idea surfaces that is not the current task, capture it as a GitHub issue labeled `inbox` in one line and return to the work. See `docs/backlog-and-project-management.md`.
- **Closing:** Rewrite `docs/session-handoff.md`, append any new decisions to `docs/decisions.md`, commit, and confirm the deploy succeeded. Never end a session with uncommitted work and no handoff.

## Docs index

- `docs/about-me.md` - who I am and how to work with me
- `docs/project-charter.md` - what we are building and why
- `docs/backlog-and-project-management.md` - how work is captured and organized
- `docs/ui-ux-guidelines.md` - design preferences
- `docs/release-practices.md` - definition of done, deploy, when to ship
- `docs/security-and-data.md` - secrets, data rules, pre-share checklist
- `docs/decisions.md` - settled choices, append-only
- `docs/session-handoff.md` - current state, rewritten every session
