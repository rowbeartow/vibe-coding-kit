# Vibe Coding Kit

A starter set of context docs for building apps with AI. Explore an idea in a throwaway chat, and when it earns a real project, clone this kit, run one bootstrap prompt, and let your AI interview you into a fully set up project.

AI output quality tracks input context. Most vibe coding advice tells you to "provide context" without telling you what that context should be. This kit is the answer: nine documents covering what experienced developers carry in their heads, written down where AI coding tools can use them.

It works whether you have never written code or you have shipped software for years. The About Me doc is what calibrates everything else to you.

## How to use it

**Before the project exists:** read `docs/exploration.md` and work the idea in a plain, disposable chat. Most ideas should die there cheaply. When one passes the graduation test, run the handoff prompt at the end of that doc and save the output.

**When an idea earns a repo:**

1. Clone this repo (or use it as a template) as the starting point for your project.
2. Open your AI tool in the project and paste the bootstrap prompt below. It runs the setup interviews in the right order, one doc at a time. You answer questions and approve drafts. It does the writing.
3. Build. `CLAUDE.md` is the index your AI reads every session. It points to everything else.
4. Keep the docs alive. The handoff gets rewritten every session, decisions get appended as they are made. A doc that stops changing stops helping.

## The bootstrap prompt

Paste this into your AI tool in a fresh clone:

> I just cloned the Vibe Coding Kit as the starting point for a new project. Read README.md and CLAUDE.md, then set this project up with me:
>
> 1. Ask whether I have an About Me doc from a previous project. If I do, I'll paste it; review it with me for anything stale and save it. If not, run the interview in docs/about-me.md.
> 2. Ask whether I have exploration notes (the handoff output from docs/exploration.md). If I do, use them as inputs to the charter interview instead of asking me those questions again. If not, run the exploration moves briefly first.
> 3. Run the interview in docs/project-charter.md, including the six settle-first questions, and record each settled decision in docs/decisions.md.
> 4. Run the interviews in docs/backlog-and-project-management.md, docs/ui-ux-guidelines.md, docs/release-practices.md, and docs/security-and-data.md.
> 5. Fill in CLAUDE.md from everything we settled.
> 6. Finish by writing the first docs/session-handoff.md, with the exact next action being the deploy-first setup in docs/release-practices.md.
>
> One doc at a time, one question at a time. Draft each doc for my approval before moving to the next. Skip anything my exploration notes or About Me already answer.

## How the docs behave

The templates are global: same guardrails and interview prompts for every project. The filled-in copies are per-project. But the docs split into four types, and they behave differently:

1. **Method docs, never filled in:** Exploration. Instructions for you, not context for the AI.
2. **Written once, copied forward:** About Me, and the personal-preference parts of UI/UX and backlog. On your second project, paste them from your first and skim for anything stale. Do not re-interview yourself.
3. **Written fresh per project:** Project Charter, the data rules in Security, the verification path in Release Practices, the project half of CLAUDE.md.
4. **Written by the work itself:** Decisions Log and Session Handoff. Never pre-written, always current.

## The docs

| Doc | Type | What it does |
| --- | --- | --- |
| `docs/exploration.md` | Method | The phase before the project exists. Prove the idea in a disposable chat, or kill it cheaply. |
| `CLAUDE.md` | Per-project | Root index. Project identity, commands, constraints. Loads every session. |
| `docs/about-me.md` | Copied forward | Your experience level and how you want to work. Calibrates everything. |
| `docs/project-charter.md` | Per-project | The problem, the users, what done means, what is out of scope. |
| `docs/backlog-and-project-management.md` | Mostly copied forward | How work is captured and organized. GitHub Issues, cheap capture, deliberate grooming. |
| `docs/ui-ux-guidelines.md` | Mostly copied forward | Your design preferences, stated once instead of relitigated every screen. |
| `docs/release-practices.md` | Per-project | Deploy-first setup, definition of done, when to ship. |
| `docs/security-and-data.md` | Per-project | Secrets, data rules, test data, and the checklist before anything goes public. |
| `docs/decisions.md` | Written by the work | Append-only log of settled choices, so they stay settled. |
| `docs/session-handoff.md` | Written by the work | Rolling state between sessions. Rewritten at the end of each one. |

## Why docs instead of one big prompt

A planning prompt gets one app built. These docs get every app built. They travel with the code, load automatically in tools like Claude Code, survive between chat sessions, and improve as you learn what works. The one-paragraph spec prompt is a snapshot. This is a system.
