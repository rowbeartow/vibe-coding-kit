# CLAUDE.md

This file loads every session. Keep it short and current.

> **Template-source note.** This repository is the kit itself, so the docs are the shipped templates. `docs/session-handoff.md` and `docs/decisions.md` stay unfilled here, and the session protocol's file targets do not apply in this repo: session state lives in chat handoff blocks, and capture goes to GitHub issues labeled `inbox`. Delete this block when bootstrapping a real project; the CLAUDE.md rewrite in the bootstrap prompt covers it.

## Rules

Read `docs/agent-rules.md` first. It is the canonical behavior spec: change protocol, stop conditions, two-failure rule, session protocol. Then read `docs/about-me.md` for who you are working with and how to deliver instructions.

## Project

<!-- One paragraph: what this app is, who uses it, what problem it solves. Pull from docs/project-charter.md once written. Anything longer than a paragraph belongs in the charter, not here. -->

## Architecture and stack

<!-- Filled in once decided. Stack, deploy target, data layer, auth approach. One line each. No reasoning and no diagrams: docs/decisions.md holds the why, docs/system-map.md the wiring. -->

## Commands

<!-- Exact commands to run, test, and deploy, one line each with what it does. Filled in as commands become real: the secret scan at bootstrap, the dependency audit at first scaffold, run and test and deploy once they exist. Nothing speculative: only commands that actually run in this project today. -->

## Project constraints

- Never ask me to paste a secret or API key into chat. I enter those in the provider's interface myself. If a task seems to need a secret in code, stop and say so.
- Follow `docs/security-and-data.md` for anything touching secrets, data, dependencies, or public exposure.
<!-- Add project-specific constraints: files not to touch, APIs not to call, etc. -->

## Docs index

- `docs/agent-rules.md` - agent behavior spec; read first
- `docs/exploration.md` - pre-project method for the human; already done by the time a repo exists
- `docs/about-me.md` - who I am and how to work with me
- `docs/project-charter.md` - what we are building and why
- `docs/backlog-and-project-management.md` - how work is captured and organized
- `docs/ui-ux-guidelines.md` - design preferences
- `docs/release-practices.md` - definition of done, testing, rollback, when to ship
- `docs/security-and-data.md` - secrets, data rules, pre-share checklist
- `docs/system-map.md` - what talks to what; created only once the app has a database, an external service, or three or more meaningful runtime components
- `docs/decisions.md` - settled choices, append-only
- `docs/session-handoff.md` - current state, rewritten every session
