# Vibe Coding Kit

A starter system for building software with AI coding agents.

Vibe coding gets harder when a project outgrows the chat where it started. The AI needs more than a description of the feature you want next. It needs to know what you are building, what has already been decided, how cautious it should be, how the project is tested and released, and where the last session left off.

AI output quality tracks input context. Most vibe coding advice tells you to "provide context" without telling you what that context should be. This kit helps produce eleven context docs that capture the kinds of decisions, constraints, and project knowledge experienced developers often carry in their heads, and puts them where AI coding tools can use them.

The docs live alongside the code, and you do not have to write them yourself. One bootstrap prompt downloads the templates, interviews you one question at a time, and turns your answers into project-specific instructions the AI can keep using as you build.

It works whether you have never written code or have shipped software for years. `docs/about-me.md` tells the agent how much to explain, how to present technical decisions, and how much autonomy you want it to take.

## How it works

There are four parts to the workflow:

1. **Explore the idea.** Before creating a project, work through the idea in an ordinary AI chat. `docs/exploration.md` gives you a lightweight method for testing the problem, finding weak spots, cutting unnecessary scope, and deciding whether the idea is worth building.
2. **Bootstrap the project.** When you are ready to build, create an empty folder, open it in an AI coding tool, and paste the bootstrap prompt below. The agent downloads the kit and interviews you to create the project context.
3. **Build with the docs in place.** The agent works from a shared set of rules, project decisions, release practices, security constraints, and your preferred way of working.
4. **Keep project state current.** Decisions are recorded as they are made, and a short session handoff keeps the next coding session from having to reconstruct the last one.

The goal is not more documentation. It is less re-explaining, fewer silent assumptions, and a project that remains understandable as the code and conversation grow.

## Start a project

### 1. Explore first, if you can

Read `docs/exploration.md` and work through your idea in a normal AI chat before creating the project.

If the idea survives that process, use the handoff prompt at the end of the doc. Save its output. The bootstrap will use those notes instead of making you explain the same things again.

If you skip exploration, that is fine. The bootstrap will run a shorter version before creating the project charter.

### 2. Open an empty project folder in an AI coding tool

Create a new empty folder on your computer for the project.

Open that folder in an AI coding tool that can read and edit files and run commands on your computer. Claude Code, Cursor, and GitHub Copilot in VS Code can all work when used in agent mode with the necessary file and terminal access.

A normal browser chat is not enough for this step. The agent needs access to the project folder.

### 3. Paste the bootstrap prompt

Copy the entire prompt below and give it to the agent.

You do not need to edit it or understand every technical instruction in it. The prompt is primarily for the coding agent. It tells the agent what to download, what to ask you, what decisions to record, and when to stop.

No GitHub account is required to get started.

## Bootstrap prompt

```text
I am starting a new project with the Vibe Coding Kit:
https://github.com/rowbeartow/vibe-coding-kit

This folder is the project folder. Bootstrap the project with me.

1. DOWNLOAD THE KIT

Download the following files from:
https://raw.githubusercontent.com/rowbeartow/vibe-coding-kit/main/

Preserve each file's relative path:

CLAUDE.md
AGENTS.md
.github/copilot-instructions.md
.gitignore
.env.example
docs/about-me.md
docs/agent-rules.md
docs/backlog-and-project-management.md
docs/decisions.md
docs/exploration.md
docs/project-charter.md
docs/release-practices.md
docs/security-and-data.md
docs/session-handoff.md
docs/system-map.md
docs/ui-ux-guidelines.md

Do not download the kit's README.md or LICENSE. This project will get
its own.

If you cannot fetch these files directly, stop and give me the
simplest fallback rather than continuing with missing files.

Initialize a git repository in this folder if one does not already
exist.

Then read CLAUDE.md and docs/agent-rules.md before continuing.

2. CALIBRATE TO ME

Before interviewing me, check for stable information about how I work
that is already available to you.

Possible sources include:
- an About Me doc from another Vibe Coding Kit project that I can
  paste
- user-level or global instruction files your tool can access
- your existing memory of my working preferences, if available

Only carry forward stable, non-sensitive information about how I work
with coding agents.

Do not import private, confidential, health, credential,
employer-secret, or similarly sensitive information. Assume
docs/about-me.md may eventually be committed to a public repository.

Show me what you propose carrying forward before writing it to
docs/about-me.md. After I approve it, interview me only for missing
or stale parts using the interview in that doc.

If nothing useful is available, run the About Me interview in full.

This reuse applies only to stable personal working preferences.
Project-specific docs below are always created fresh.

3. RESOLVE THE IDEA

Ask whether I have exploration notes produced from
docs/exploration.md.

If I do, use them as inputs to the project charter instead of asking
me the same questions again.

If I do not, run a brief exploration now. Interview me about the
problem and intended user, probe weak spots, reduce unnecessary
scope, and decide whether the remaining idea passes the graduation
test in docs/exploration.md.

Skip the throwaway prototype during bootstrap.

Feed the resulting answers directly into the charter interview rather
than creating a separate exploration document.

4. CREATE THE PROJECT CHARTER

Run the interview in docs/project-charter.md, including its
settle-first questions.

Record every settled architectural or project decision in
docs/decisions.md as it is made.

5. CONFIGURE HOW THE PROJECT WILL BE BUILT

Run the interviews in this order:

1. docs/backlog-and-project-management.md
2. docs/ui-ux-guidelines.md
3. docs/release-practices.md
4. docs/security-and-data.md

For release practices, include the rollback questions.

For security and data, establish the secret-scanning command
appropriate for the chosen stack and record it in CLAUDE.md.

Do not invent a dependency-audit command before a package manifest
exists. Add that later when the project is first scaffolded, as
specified in docs/security-and-data.md.

If a preference was already established in About Me or earlier in
this bootstrap, confirm it rather than asking me the same question
again.

6. SET UP PROJECT TRACKING

Ask whether I have a GitHub account.

GitHub is optional and creating an account is not a bootstrap
requirement.

If I have GitHub:
- Help me create a repository for this project if one does not
  already exist.
- Defaults unless I say otherwise:
  - my personal account
  - repository name matches the project
  - private repository
  - created empty, without its own README or .gitignore
- Point this project's origin at that repository.
- Use GitHub Issues as the tracker unless I name another tracker.
- Create the `inbox` and `needs-decision` labels.
- If you cannot create them through authenticated GitHub tooling,
  give me exact web UI steps.
- Turn capture-list items worth revisiting into `inbox` issues.

If I do not have GitHub:
- Create BACKLOG.md in the project root.
- Use it as the project's tracker.
- Put one captured item per entry.
- Note at the top that it can be migrated to GitHub Issues later.
- Record in CLAUDE.md that BACKLOG.md is the active tracker.

Ideas we considered and deliberately rejected do not need backlog
entries.

7. LEAVE THE SYSTEM MAP DORMANT UNTIL NEEDED

Do not fill in docs/system-map.md unless the project already has at
least one of these:
- a database
- an external service the application itself calls at runtime
- three or more meaningful runtime components

The deployment platform and GitHub do not count as runtime components
for this trigger.

Until the trigger is met, leave the template untouched.

8. BUILD THE PROJECT INDEX

Fill in CLAUDE.md from the decisions made during bootstrap.

Remove its template-source note.

Keep CLAUDE.md concise. It should contain current project identity,
stack, commands, constraints, and links to the deeper project docs
rather than duplicating them.

Write a new README.md for this project with a short explanation of:
- what the project is
- who it is for
- what problem it solves

Add setup and run instructions later, once an application actually
exists.

9. CREATE THE FIRST HANDOFF

Write the first docs/session-handoff.md.

The exact next action should be the first step of the deploy-first
process in docs/release-practices.md.

Do not start scaffolding features, installing the application stack,
or building the product during bootstrap. Bootstrap ends with the
project context ready and the next action identified.

10. FINISH CLEANLY

Review the project diff.

Make sure no secrets, private information, template interview prompts
that should have been removed, or accidental kit README/LICENSE files
are present.

Commit the completed bootstrap documents.

The session handoff should name the branch and the final commit
subject.

BOOTSTRAP INTERVIEW RULES

Work one document at a time and ask one question at a time.

Ask every question in plain language.

If I cannot answer a technical question, recommend one option with a
one-line reason and ask me to confirm it rather than presenting a
large menu of choices.

Draft each document for my approval before moving to the next.

When I approve a document, remove its interview-prompt block, from
the prompt heading through the quoted prompt, while keeping its
Purpose line.

Until the tracker exists, keep any ideas or issues that surface in a
temporary capture list in this conversation.

Do not ask a question that has already been answered earlier in the
bootstrap, including through About Me, approved carried-forward
preferences, exploration notes, or another interview.
```

**If you build with AI tools all day:** the prompt is the whole front door, so there is nothing to install. If you would rather invoke it than paste it, wrap it yourself as a global skill or rule in your tool of choice, pointing at this repo. The kit does not ship or maintain tool-specific wrappers; this repo stays the single source of truth, and the prompt fetches the current docs at runtime.

## What the kit contains

The kit uses several small documents instead of one giant instruction prompt. Each has a specific lifecycle.

| File | Lifecycle | Purpose |
| --- | --- | --- |
| `docs/exploration.md` | Fixed | A pre-project method for testing an idea before committing to a codebase. |
| `docs/agent-rules.md` | Fixed | Canonical agent behavior: change protocol, stop conditions, failure handling, verification, and session discipline. |
| `CLAUDE.md` | Project-specific | Short project index containing identity, stack, commands, constraints, and pointers to deeper docs. |
| `AGENTS.md` | Fixed adapter | Points agents that use the `AGENTS.md` convention to the shared rules and project context. |
| `.github/copilot-instructions.md` | Fixed adapter | Points GitHub Copilot at the same shared rules and project context. |
| `docs/about-me.md` | Carried forward | Your technical experience and preferred way of working with an AI coding agent. |
| `docs/project-charter.md` | Project-specific | Problem, users, success criteria, scope, lifespan, risk, and major technical choices. |
| `docs/backlog-and-project-management.md` | Mostly carried forward | How work is captured, groomed, prioritized, and tracked. |
| `docs/ui-ux-guidelines.md` | Mostly carried forward | Reusable design preferences plus any project-specific UI constraints. |
| `docs/release-practices.md` | Project-specific | Deployment, definition of done, testing, rollback, and shipping rules. |
| `docs/security-and-data.md` | Project-specific | Secrets, data handling, dependencies, test data, and checks before public exposure. |
| `docs/system-map.md` | Filled on trigger | Runtime components and how they communicate. Left as a template until the project becomes complex enough to need it. |
| `docs/decisions.md` | Grows with the project | Append-only record of settled decisions and why they were made. |
| `docs/session-handoff.md` | Rewritten each session | Current state, unfinished work, and the exact next action for the next session. |

The templates start the same, but the project-specific copies evolve with the application. Stable working preferences can carry from one project to the next; architecture, security, release decisions, and current state should be grounded in the project actually being built.

## How the agent uses them

`docs/agent-rules.md` is the canonical behavior specification.

`CLAUDE.md` holds the concise project-specific context and points to the deeper documents. The kit also includes `AGENTS.md` and `.github/copilot-instructions.md` so tools that support those conventions can find the same shared rules instead of maintaining separate versions of them.

The result is one project context with multiple tool entry points, rather than different instructions slowly drifting apart.

## Why separate docs instead of one big prompt?

A single planning prompt is a snapshot. A software project is not.

Scope changes. Commands become real. Architectural decisions accumulate. Bugs expose new constraints. Release procedures change. One session ends and another begins.

Keeping those concerns in small, versioned documents means the context travels with the code and can change with it. The AI does not have to reconstruct the project from chat history, and you do not have to remember every decision yourself.

That is the purpose of the kit: give the coding agent enough durable context to work consistently without turning a small project into a documentation project.
