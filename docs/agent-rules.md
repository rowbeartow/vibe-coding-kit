# Agent Rules

The canonical behavior spec for any AI agent working in this repository. Tool adapters (CLAUDE.md, AGENTS.md, .github/copilot-instructions.md) point here. If an adapter and this file disagree, this file wins.

## Change Protocol

Every change follows the same five steps.

1. **Understand.** Restate the task in a line or two. Read the docs that govern it before touching code.
2. **Preflight.** Name the files you intend to change before changing them. If the change touches architecture, schema, auth, infrastructure, dependencies, secrets, billing, or production data, say so explicitly and check the stop conditions below.
3. **Implement.** Make the smallest coherent change that completes the task. No bundled refactors, no drive-by fixes.
4. **Verify.** Run the exact project commands from CLAUDE.md. Exercise the affected path end to end, not just the component that changed. Inspect the diff before committing. Report what you verified and what you assumed, as two separate lists.
5. **Finish.** Append any new decision to `docs/decisions.md`, update or close the related issue, and update `docs/session-handoff.md` if the session is ending.

## Stop conditions

Never act silently on any of the following. Stop, state what you intend to do and why, and wait for approval. These apply regardless of the autonomy preference in `docs/about-me.md`.

- Schema changes or any deletion of data
- Auth or permission changes
- Adding an external service, or anything that creates a new cost
- Major dependency additions or upgrades
- Deploy infrastructure changes
- Exposing anything publicly that is not already public
- Destructive git operations: force push, history rewrite, deleting branches with unmerged work
- Reversing anything recorded in `docs/decisions.md`
- Expanding scope beyond the stated task

## Two-failure rule

When the same operation fails twice, stop making changes. Then:

1. Preserve the exact command, exit status, and full error output.
2. State your hypothesis for the cause.
3. Separate the symptom from the root cause. They are usually not the same thing.
4. Propose a different approach and get agreement before touching anything else.

Do not run the same operation a third time with minor variations and hope.

## Sessions

The invariant is: never lose state.

**Opening.** Read `docs/session-handoff.md`. State back the objective, current state, and next action before starting work.

**During.** When a bug or idea surfaces that is not the current task, capture it as a GitHub issue labeled `inbox` in one line and return to the work. See `docs/backlog-and-project-management.md`.

**Ending.** A session ends one of two ways:

1. **Completed and verified.** The change is done, verification ran, the work is committed and deployed per `docs/release-practices.md`, and the handoff is updated.
2. **Incomplete, on a branch.** The work is committed to a branch, and the handoff says honestly what is done, what is not, and the exact next action.

Outside a bootstrap session there is no third ending. Never leave uncommitted work, and never write a handoff that claims more than was verified.

**Bootstrap session.** The first session in a fresh copy of the kit runs before most of the above can exist, so for that session only:

- The bootstrap prompt in the README is the session objective. There is no handoff to read and no issue to name.
- Verification means reviewing each drafted doc with the user before approval. There are no project commands to run yet.
- Per-session issue linkage starts once the tracker exists, partway through the bootstrap.
- A third session ending exists, for bootstrap only: **bootstrap complete.** The docs are filled, approved, and committed, and deploy is not yet expected. The handoff names the branch and the final commit's subject line, because the commit that contains the handoff cannot contain its own hash.
