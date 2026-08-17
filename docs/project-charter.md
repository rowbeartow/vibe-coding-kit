# Project Charter

**Purpose:** One page that answers what we are building, for whom, and what done means. Its most valuable section is Out of Scope, because AI tools will happily build everything you mention and half of it will be things you did not need.

**Interview prompt.** Paste this into your AI tool:

> Interview me one question at a time to write the project charter. Start with the problem I am trying to solve and who has it. Then: what the app takes in, what it does, what comes out, and what success looks like. Push me on scope: ask what I am tempted to include that v1 does not need, and challenge anything that does not serve the core problem. Then ask me the eight settle-first questions in docs/project-charter.md. Then draft the charter for my approval.

---

## Problem

<!-- What is slow, repetitive, or error-prone today, and for whom. If you cannot name a real person (including yourself) who hits this problem, stop and find one. -->

## Users

<!-- Who uses this. "Just me" is a complete and honest answer that simplifies everything downstream. -->

## What it does

<!-- Inputs, process, outputs, in plain language. Three or four sentences. -->

## Success criteria for v1

<!-- Observable statements. "I can paste meeting notes and get a task list with owners in under a minute" beats "the app works well." -->

## Out of scope for v1

<!-- Explicit list. Everything you were tempted to include and cut. The AI should refuse to build these without a conversation first. -->

## Settle before building

Decide these eight before any code exists. Record each in `docs/decisions.md`.

1. **Objective.** One paragraph. What exists at the end, and who uses it.
2. **Definition of done for v1**, including the out-of-scope list above.
3. **Deploy target.** Where this runs. It constrains the architecture, so it goes first, not last.
4. **Stack.** The language and framework this gets built with. Stack and deploy target constrain each other, so they get decided together. If you do not write code, have the AI recommend one stack with a one-line reason and approve it rather than choosing from a menu.
5. **Data layer.** Where data lives, if anywhere. Do not add a database speculatively.
6. **Auth.** Real accounts, a shared-secret gate, or none. Retrofitting auth is the most expensive common rewrite, so decide now even if the answer is none.
7. **Lifespan.** Experiment, personal tool, or maintained app. If experiment, skip most of the ceremony in this kit and just build.
8. **Risk.** Local-only, internet-exposed, multi-user, or handling sensitive data. Ceremony scales with risk, not lifespan: internet-exposed means the security checklist runs before any URL is shared, multi-user means auth gets tested as someone other than you, sensitive data means the data rules are filled in before the first real record is stored. These are separate axes. A weekend experiment that touches real customer data is still high risk.
