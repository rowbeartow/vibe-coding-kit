# Vibe Coding Kit

A starter set of context docs for building apps with AI. Clone it, have your AI interview you to fill in each doc, then build your project on top of it.

AI output quality tracks input context. Most vibe coding advice tells you to "provide context" without telling you what that context should be. This kit is the answer: seven documents that experienced developers carry in their heads and that AI coding tools work dramatically better with when written down.

It works whether you have never written code or you have shipped software for years. The About Me doc is what calibrates everything else to you.

## How to use it

1. **Clone this repo** (or use it as a template) as the starting point for your project.
2. **Fill in the docs by interview, not by hand.** Open each doc, copy the interview prompt at the top, and paste it into your AI tool. Answer its questions, let it draft the doc, review, and approve. You make the calls. It does the writing.
3. **Fill them in this order:** About Me, Project Charter, Backlog and Project Management, UI/UX Guidelines, Release Practices. The Decisions Log and Session Handoff fill themselves as you work.
4. **Build.** `CLAUDE.md` is the index your AI reads every session. It points to everything else.
5. **Keep the docs alive.** Update the handoff at the end of every session. Append decisions as you make them. A doc that stops changing stops helping.

## The docs

| Doc | What it does |
| --- | --- |
| `CLAUDE.md` | Root index. Project identity, commands, constraints. Loads every session. |
| `docs/about-me.md` | Your experience level and how you want to work. Calibrates everything. |
| `docs/project-charter.md` | The problem, the users, what done means, what is out of scope. |
| `docs/backlog-and-project-management.md` | How work gets captured and organized. GitHub Issues, cheap capture, deliberate grooming. |
| `docs/ui-ux-guidelines.md` | Your design preferences, stated once instead of relitigated every screen. |
| `docs/release-practices.md` | Deploy-first setup, definition of done, when to ship. |
| `docs/decisions.md` | Append-only log of settled choices, so they stay settled. |
| `docs/session-handoff.md` | Rolling state between work sessions. Rewritten at the end of each one. |

## Why docs instead of one big prompt

A planning prompt gets one app built. These docs get every app built. They travel with the code, load automatically in tools like Claude Code, survive between chat sessions, and improve as you learn what works. The one-paragraph spec prompt is a snapshot. This is a system.
