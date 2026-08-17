# Vibe Coding Kit

A starter set of context docs for building apps with AI. Explore an idea in a prototyping chat, and when you want to bring it to life in a real project, clone this kit, run one bootstrap prompt, and let your AI interview you into a fully set up project.

AI output quality tracks input context. Most vibe coding advice tells you to "provide context" without telling you what that context should be. This kit is the answer: eleven documents covering what experienced developers carry in their heads, written down where AI coding tools can use them.

It works whether you have never written code or you have shipped software for years. The About Me doc is what calibrates everything else to you.

## How to use it

**Before the project exists:** read `docs/exploration.md` and work the idea in a plain, disposable chat. Most ideas should die there cheaply. When one passes the graduation test, run the handoff prompt at the end of that doc and save the output.

**When an idea earns a repo:**

1. Clone this repo (or use it as a template) as the starting point for your project.
2. Open your AI tool in the project and paste the bootstrap prompt below. It runs the setup interviews in the right order, one doc at a time. You answer questions and approve drafts. It does the writing.
3. Build. `docs/agent-rules.md` governs how the AI behaves. `CLAUDE.md` is the index it reads every session; `AGENTS.md` and `.github/copilot-instructions.md` point other tools at the same rules.
4. Keep the docs alive. The handoff gets rewritten every session, decisions get appended as they are made. A doc that stops changing stops helping.

## The bootstrap prompt

Paste this into your AI tool in a fresh clone:

> I just cloned the Vibe Coding Kit as the starting point for a new project. Read README.md, CLAUDE.md, and docs/agent-rules.md, then set this project up with me:
>
> 1. Ask whether I have an About Me doc from a previous project. If I do, I'll paste it; review it with me for anything stale and save it. If not, run the interview in docs/about-me.md.
> 2. Ask whether I have exploration notes (the handoff output from docs/exploration.md). If I do, use them as inputs to the charter interview instead of asking me those questions again. If not, run a brief exploration first: interview me about the idea, probe its weak spots, and cut it until it hurts. Skip the throwaway prototype, and feed the answers straight into the charter interview rather than writing a separate doc.
> 3. Run the interview in docs/project-charter.md, including the eight settle-first questions, and record each settled decision in docs/decisions.md.
> 4. Run the interviews in docs/backlog-and-project-management.md, docs/ui-ux-guidelines.md, docs/release-practices.md (including the two rollback questions), and docs/security-and-data.md (including setting up the secret-scanning and dependency-audit commands for this stack).
> 5. Check whether this folder is connected to its own GitHub repository. If there is no remote, or origin still points at the Vibe Coding Kit, walk me through creating a repository on github.com and pointing origin at it, then continue.
> 6. Set up the tracker. GitHub Issues is the default; adapt only if I name a different tracker. Create the `inbox` and `needs-decision` labels now, because the session protocol depends on them existing. Then file everything on the capture list as `inbox` issues.
> 7. Skip docs/system-map.md unless the project already meets its trigger: a database, an external service, or a third component.
> 8. Fill in CLAUDE.md from everything we settled, and rewrite README.md to describe this project: what it is, who it is for, and how to run it, in a short paragraph drawn from the charter.
> 9. Finish by writing the first docs/session-handoff.md, with the exact next action being the deploy-first setup in docs/release-practices.md.
>
> One doc at a time, one question at a time. Draft each doc for my approval before moving to the next; when a doc is approved, remove its interview-prompt block and keep its Purpose line. Until the tracker exists, hold any ideas or issues that surface in a running capture list. Skip anything my exploration notes or About Me already answer.

## How the docs behave

The templates are global: same guardrails and interview prompts for every project. The filled-in copies are per-project. But the docs split into five types, and they behave differently:

1. **Fixed, never filled in:** Exploration (method for you) and Agent Rules (behavior spec for the AI). Identical in every project.
2. **Written once, copied forward:** About Me, and the personal-preference parts of UI/UX and backlog. On your second project, paste them from your first and skim for anything stale. Do not re-interview yourself.
3. **Written fresh per project:** Project Charter, the data rules in Security, the verification path and rollback answers in Release Practices, the project half of CLAUDE.md.
4. **Created on trigger:** System Map. Does not exist until the app has a database, an external service, or a third component.
5. **Written by the work itself:** Decisions Log and Session Handoff. Never pre-written, always current.

## The docs

| Doc | Type | What it does |
| --- | --- | --- |
| `docs/exploration.md` | Method | The phase before the project exists. Prove the idea in a disposable chat, or kill it cheaply. |
| `docs/agent-rules.md` | Fixed | Canonical agent behavior: change protocol, stop conditions, two-failure rule, session protocol. |
| `CLAUDE.md` | Per-project | Root index. Project identity, commands, constraints. Loads every session. |
| `AGENTS.md`, `.github/copilot-instructions.md` | Fixed | Adapters pointing other AI tools at agent-rules and CLAUDE.md. |
| `docs/about-me.md` | Copied forward | Your experience level and how you want to work. Calibrates everything. |
| `docs/project-charter.md` | Per-project | The problem, the users, what done means, what is out of scope, lifespan and risk. |
| `docs/backlog-and-project-management.md` | Mostly copied forward | How work is captured and organized. GitHub Issues, cheap capture, deliberate grooming. |
| `docs/ui-ux-guidelines.md` | Mostly copied forward | Your design preferences, stated once instead of relitigated every screen. |
| `docs/release-practices.md` | Per-project | Deploy-first setup, definition of done, testing, rollback, when to ship. |
| `docs/security-and-data.md` | Per-project | Secrets, data rules, test data, and the checklist before anything goes public. |
| `docs/system-map.md` | Created on trigger | What talks to what. Exists only once the app has a database, external service, or third component. |
| `docs/decisions.md` | Written by the work | Append-only log of settled choices, so they stay settled. |
| `docs/session-handoff.md` | Written by the work | Rolling state between sessions. Rewritten at the end of each one. |

## Why docs instead of one big prompt

A planning prompt gets one app built. These docs get every app built. They travel with the code, load automatically in tools like Claude Code, survive between chat sessions, and improve as you learn what works. The one-paragraph spec prompt is a snapshot. This is a system.
