# Security and Data

**Purpose:** The doc most likely to save you from real damage. AI coding tools create security problems casually: they hardcode API keys to make an example work, generate realistic-looking test data, stub out auth "for now," and leave debug output in production. None of that is malicious. All of it ships if nobody is watching. This doc is the watching.

**Interview prompt.** Paste this into your AI tool:

> Read docs/security-and-data.md and interview me one question at a time to fill in the specifics: what data this app touches, whether any of it belongs to other people, whether any of it is sensitive (health, financial, personal contact info), where the app is deployed and who can reach it, and whether my work or industry has rules about data handling. Then update the doc and flag anything about my answers that changes the risk level.

---

## Secrets

- API keys, passwords, and tokens never appear in code, in committed files, or in chat with an AI. They go in environment variables, entered directly in the provider's interface.
- The repo carries a `.env.example` with variable names and no values. `.env` is in `.gitignore` and never committed.
- If a secret does get committed: rotate it immediately at the provider. Deleting the commit is not enough; git history and forks keep it alive. Rotation is the fix, deletion is cleanup.
- The AI's standing instruction: if a task seems to need a secret in code, stop and say so instead of hardcoding a placeholder that becomes permanent.

## Data rules

<!-- Fill in for this app: -->

- **What this app stores:** <!-- List it. If the answer is "nothing persistent," say so; that is the best answer available. -->
- **Whose data it is:** <!-- Only yours, or other people's? Other people's data raises every stake below. -->
- **Never store:** <!-- Defaults worth keeping: passwords in plain text, full payment card numbers, anything you would not want in a breach notification. Add your own. -->

## Test data

- Never use real personal, customer, or company data as test data.
- Be suspicious of AI-generated test data: models produce realistic names, emails, and numbers, and sometimes those are real. Use obviously fake values (`test-user-1@example.com`) so leftover test data is recognizable at a glance.
- Test data is a build leftover. Removing it is part of the pre-share checklist below, and the deploy-time bug where the app reads leftover test data instead of real input is common enough to check for specifically.

## Before anything goes public

Run this checklist before sharing a URL beyond yourself, and again before opening it wider:

1. Search the codebase for keys and tokens (`sk-`, `key`, `secret`, `token`, `password`). Anything found gets moved to environment variables and rotated.
2. Confirm auth actually gates what it should. Test as a second account and as a logged-out visitor, not just as yourself.
3. Remove or protect debug routes, admin pages, and verbose error output. Stack traces on a public page are a map for attackers.
4. Purge test data.
5. Confirm the app is not logging sensitive values (inputs, tokens, personal data) anywhere logs persist.
6. Ask the AI directly: "Review this app for security problems before I share it publicly. Assume a hostile stranger has the URL." It catches its own shortcuts surprisingly well when asked.

## Dependencies

AI tools add packages liberally, and every package is code you are trusting. Standing instruction: prefer the standard library and packages already in the project; flag any new dependency and why it is needed rather than silently adding it.

## If something goes wrong

Assume it eventually will. The order of operations: rotate any exposed secrets first, take the app private or offline second, figure out what happened third. If other people's data was involved, tell them; if your work has rules about incidents, follow them. Speed on the first step matters more than understanding on the third.
