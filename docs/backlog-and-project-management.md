# Backlog and Project Management

**Purpose:** How work gets captured, organized, and chosen. For a one-person AI-assisted project the whole system is GitHub Issues plus two habits: capture is cheap, grooming is deliberate.

**Interview prompt.** Paste this into your AI tool:

> Interview me briefly to adapt the backlog doc in docs/backlog-and-project-management.md. Ask: do I already use GitHub Issues or another tracker, do I tend to generate ideas mid-task that get lost, and do I want to work in timeboxed sprints or a simple ordered queue? Then adjust the doc to match and show me the result.

---

## Capture: cheap, immediate, no ceremony

Ideas, bugs, and to-dos surface while you are working on something else. The rule for the AI:

1. When one surfaces, create a GitHub issue immediately. Title is the outcome. Body is one or two lines of context. Label `inbox`.
2. Say the issue number in one line and return to the current task.
3. No acceptance criteria, no clarifying questions, no stopping the work.

Capture has to stay cheap or the habit dies. Ceremony belongs in grooming, not capture.

## Grooming: deliberate and separate

At the start of a session, or once a week, walk the `inbox` items. Each one gets promoted, merged into an existing issue, or closed. Most get merged or closed, which is the point.

When promoting an issue to real work, add:

- What a user can do after this ships, in one sentence
- Acceptance criteria
- Any files or features that must not be touched

## Labels

Start with two:

- `inbox` - captured, not yet groomed
- `needs-decision` - the work hit a question that changes the architecture. The AI stops, labels it, and surfaces it rather than deciding silently and continuing.

Add more labels only when their absence causes an actual problem.

## Choosing what to work on

One issue per session. Name it at the top of the session, finish it or hand it off cleanly at the end. If you prefer sprints, a sprint is just a short list of issues with a date; a milestone in GitHub covers it. Do not build more process than a one-person project can feed.

## The two-patch rule

If the same bug gets fixed twice, do not fix it a third time. File an issue for the underlying pattern instead. Recurring symptoms mean the structure is wrong, and AI tools will otherwise patch the same symptom forever without telling you that.
