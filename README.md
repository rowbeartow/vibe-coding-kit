# Vibe Coding Kit

A starter set of context docs for building apps with AI. Explore an idea in a prototyping chat, and when you want to bring it to life in a real project, paste one bootstrap prompt into an AI coding tool and let it interview you into a fully set up project. No clone, no install: the prompt fetches everything it needs from this repo.

AI output quality tracks input context. Most vibe coding advice tells you to "provide context" without telling you what that context should be. This kit helps produce eleven context docs that capture the kinds of decisions, constraints, and project knowledge experienced developers often carry in their heads, and puts them where AI coding tools can use them.

It works whether you have never written code or you have shipped software for years. The About Me doc is what calibrates everything else to you.

## How to use it

**Ideally before the project exists:** read `docs/exploration.md` and work the idea in a plain, disposable chat. Arriving at the bootstrap without having done it is fine; the bootstrap runs a brief version in place. Most ideas should die there cheaply. When one passes the graduation test, run the handoff prompt at the end of that doc and save the output.

**When an idea earns a project:**

1. Get an AI tool that can open and edit a project folder. Claude Code, Cursor, and Copilot in VS Code all work. A chat tab in the browser is not enough for this part: the tool has to be able to create files on your computer.
2. Make a new, empty folder for the project and open it in that tool.
3. Copy the bootstrap prompt below and paste it in. It fetches the kit's docs into your folder, then runs the setup interviews in the right order, one doc at a time. You answer questions and approve drafts; it does the writing. No GitHub account is required: without one, your backlog lands in a local file that upgrades to GitHub Issues whenever you get an account.
4. Build. `docs/agent-rules.md` governs how the AI behaves. `CLAUDE.md` is the index it reads every session; `AGENTS.md` and `.github/copilot-instructions.md` point other tools at the same rules.
5. Keep the docs alive. The handoff gets rewritten every session, decisions get appended as they are made. A doc that stops changing stops helping.

## The bootstrap prompt

Copy this whole block and paste it into your AI tool, opened in the new project folder:

```text
I am starting a new project with the Vibe Coding Kit
(https://github.com/rowbeartow/vibe-coding-kit). This folder is the
project folder. Set it up with me:

1. Fetch the kit into this folder from
   https://raw.githubusercontent.com/rowbeartow/vibe-coding-kit/main/
   saving each file at the same relative path: CLAUDE.md, AGENTS.md,
   .github/copilot-instructions.md, .gitignore, .env.example, and the
   eleven docs: docs/about-me.md, docs/agent-rules.md,
   docs/backlog-and-project-management.md, docs/decisions.md,
   docs/exploration.md, docs/project-charter.md,
   docs/release-practices.md, docs/security-and-data.md,
   docs/session-handoff.md, docs/system-map.md,
   docs/ui-ux-guidelines.md. Do not fetch the kit's README.md or
   LICENSE; this project gets its own. Initialize a git repository
   here if there is not one already. Then read CLAUDE.md and
   docs/agent-rules.md before going on.

2. Inventory before interview. Before asking me anything, check what
   is already known about me: an About Me doc I can paste from a
   previous kit project, global instruction files (a CLAUDE.md in my
   home directory, Copilot global instructions), and your own memory
   of me where you have one. State back what you found, save what
   applies into docs/about-me.md, and interview me only for the gaps,
   using the interview in that doc. If nothing turned up, run the
   interview in full. The inventory covers the stable about-me
   material only; the per-project docs below are always interviewed
   fresh.

3. Ask whether I have exploration notes (the handoff output from
   docs/exploration.md). If I do, use them as inputs to the charter
   interview instead of asking me those questions again. If not, run
   a brief exploration first: interview me about the idea, probe its
   weak spots, and cut it until it hurts; skip the throwaway
   prototype and judge the graduation test on the remaining signals.
   Feed the answers straight into the charter interview rather than
   writing a separate doc.

4. Run the interview in docs/project-charter.md, including the eight
   settle-first questions, and record each settled decision in
   docs/decisions.md.

5. Run the interviews in docs/backlog-and-project-management.md,
   docs/ui-ux-guidelines.md, docs/release-practices.md (including the
   two rollback questions), and docs/security-and-data.md (including
   setting up the secret-scanning command for this stack; the
   dependency audit is recorded later, at first scaffold, per that
   doc). Where the inventory already answered a preference question,
   confirm it instead of re-asking.

6. Ask whether I have a GitHub account. Having one is not required,
   and creating one is never a bootstrap step.
   - If I do: walk me through creating a repository on github.com and
     pointing origin at it. Defaults unless I say otherwise: my
     personal account, named after the project, private, created
     empty with no README or .gitignore of its own. Then set up the
     tracker. GitHub Issues is the default; adapt only if I name a
     different tracker. Create the `inbox` and `needs-decision`
     labels now, because the session protocol depends on them
     existing; if you cannot write to GitHub from here, give me exact
     web-UI steps to create them myself. Then file each capture-list
     item worth revisiting as an `inbox` issue.
   - If I do not: create BACKLOG.md in the project root as the
     tracker, one line per item, and put the capture-list items worth
     revisiting there. Note at the top of the file that it upgrades
     to GitHub Issues once an account exists.
   Either way, ideas we considered and rejected can drop.

7. Leave docs/system-map.md untouched unless the project already
   meets its trigger: a database, an external service the app itself
   calls at runtime (the deploy host and GitHub do not count), or a
   third component.

8. Fill in CLAUDE.md from everything we settled, deleting its
   template-source note, and write a README.md describing this
   project in a short paragraph drawn from the charter: what it is
   and who it is for, adding how to run it once there is an app to
   run.

9. Finish by writing the first docs/session-handoff.md, with the
   exact next action being the first step of the deploy-first setup
   in docs/release-practices.md, not the whole sequence.

One doc at a time, one question at a time. Ask every interview
question in plain language; whenever I cannot answer, recommend one
option with a one-line reason and ask me for a yes. Draft each doc
for my approval before moving on; when a doc is approved, remove its
interview-prompt block, from the prompt heading through the quoted
text, and keep its Purpose line. Until the tracker exists, hold any
ideas or issues that surface in a running capture list in this chat.
Skip any question already settled earlier in this bootstrap,
including by the inventory, my exploration notes, or About Me.
```

**If you build with AI tools all day:** the prompt is the whole front door, so there is nothing to install. If you would rather invoke it than paste it, wrap it yourself as a global skill or rule in your tool of choice, pointing at this repo. The kit does not ship or maintain tool-specific wrappers; this repo stays the single source of truth, and the prompt fetches the current docs at runtime.

## How the docs behave

The templates are global: same guardrails and interview prompts for every project. The filled-in copies are per-project. But the docs split into five types, and they behave differently:

1. **Fixed, never filled in:** Exploration (method for you) and Agent Rules (behavior spec for the AI). Identical in every project.
2. **Written once, carried forward:** About Me, and the personal-preference parts of UI/UX and backlog. On your second project, the bootstrap's inventory step pulls them forward and asks only about what is missing or stale. Do not re-interview yourself.
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
