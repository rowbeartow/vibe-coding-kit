# Release Practices

**Purpose:** A simplified release process for a small AI-assisted project. Three ideas carry all the weight: deploy is wired first, done means verified, and shipped beats polished.

**Interview prompt.** Paste this into your AI tool:

> Read docs/release-practices.md and interview me briefly to fill in the specifics: where this app will be deployed, whether anyone besides me uses it, and what a full verification pass looks like for this particular app. Then update the doc.

---

## Deploy first, then build

Get deployment working before any features exist, so it is never the unknown variable later.

1. Repo with a README, a `.gitignore` for the stack, and a `.env.example` listing variable names with no values. `.env` is never committed.
2. Commit a skeleton that renders one page or returns one response.
3. Connect the deploy target and enable auto-deploy from `main`.
4. Confirm the skeleton is live at a real URL.
5. Then start building.

Work on short-lived branches. `main` always deploys. Do not let branches accumulate.

## Definition of done

One component working is not done. Before calling anything done, walk the full path a real user takes and report which links were actually exercised and which were not. The checks that catch the most failures:

- Test in a clean browser state, not a session with existing cookies and cache.
- Test with a second account if the app has accounts. A pass under the builder's account does not prove permissions work for anyone else.
- Confirm the deployed URL reflects the change, not just the local version.
- If a link in the path was not tested, say which one rather than implying full coverage.

<!-- Add the specific verification path for this app: the steps a user takes from arrival to the core outcome. -->

## When to ship

- Ship when v1 success criteria in the charter are met, not when nothing is left to improve.
- Before sharing beyond yourself: add a first-run explanation, remove build leftovers (test data, placeholder text, debug output), and do a soft launch with one person before opening it wider.
- After each shipped change, watch what confuses real users and route it through the backlog, not straight into the code.

## Versioning, simplified

Tag releases only if someone besides you depends on the app. Otherwise, the deploy history is the version history, and that is fine.
