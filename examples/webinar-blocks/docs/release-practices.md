# Release Practices

**Purpose:** A simplified release process for a small AI-assisted project. Three ideas carry all the weight: deploy is wired first, done means verified, and shipped beats polished.

**Interview prompt.** Paste this into your AI tool:

> Read docs/release-practices.md and interview me briefly to fill in the specifics: where this app will be deployed, whether anyone besides me uses it, what a full verification pass looks like for this particular app, whether instant rollback is available on my platform, and whether the app has persistent data. Then update the doc.

---

## Deploy first, then build

Get deployment working before any features exist, so it is never the unknown variable later.

1. Repo with a README, a `.gitignore` for the stack, and a `.env.example` listing variable names with no values. `.env` is never committed.
2. Commit a skeleton that renders one page or returns one response.
3. Connect the deploy target and enable auto-deploy from `main`.
4. Confirm the skeleton is live at a real URL.
5. Then start building.

Work on short-lived branches. `main` is always deployable: anything merged there is verified and safe to ship at any moment. Do not let branches accumulate.

## Definition of done

One component working is not done. Before calling anything done, walk the full path a real user takes and report which links were actually exercised and which were not. The checks that catch the most failures:

- Test in a clean browser state, not a session with existing cookies and cache.
- Test with a second account if the app has accounts. A pass under the builder's account does not prove permissions work for anyone else.
- Confirm the deployed URL reflects the change, not just the local version.
- If a link in the path was not tested, say which one rather than implying full coverage.

Verification path for this app:

1. Open the deployed URL in a clean browser profile.
2. Create an event with every field filled.
3. Confirm all six channel blocks generate and each Copy button copies the right block.
4. Change the Broadcast link, and confirm every block that contains it shows the new link.
5. Close and reopen the browser, and confirm the event is still there.
6. Confirm the deployed URL shows the change, not just localhost.

## Testing

Tests protect expensive failures, not lines of code. Coverage percentage is not a goal in this kit. Three kinds of tests earn their keep:

- **Smoke check.** One command that proves the app starts and the main page or endpoint responds. Run it after every change.
- **Critical path.** One test per path where failure is expensive. The core workflow qualifies, and anything touching auth, data writes, or an external service boundary gets extra weight, because failures there are silent, costly, or both.
- **Regression rule.** When a real bug is fixed, add a test that would have caught it. A bug that happened once is the best predictor of a bug that happens again.

If the AI proposes a broader suite, it should justify each addition against a failure that would actually cost something.

## Rollback, lean version

Answered at bootstrap 2026-08-14, recorded in `docs/decisions.md`: instant rollback is available (Vercel Deployments, Promote to Production), and persistent data is client-side localStorage only, so rollback is redeploying, with the schema caution that localStorage does not roll back with the code.

1. **Is instant rollback available?** Most deploy platforms with a deploy history can restore the previous version in one click. Know the exact steps before you need them.
2. **Is there persistent data?** If no, rollback is just redeploying the old version and this section is done. If yes, add schema-caution rules: schema changes are additive when possible, destructive migrations wait until the code that needed the old shape is verified gone, and any migration that deletes or transforms data is a stop condition per `docs/agent-rules.md`.

## When to ship

- Ship when v1 success criteria in the charter are met, not when nothing is left to improve.
- Before sharing beyond yourself: add a first-run explanation, remove build leftovers (test data, placeholder text, debug output), and do a soft launch with one person before opening it wider.
- After each shipped change, watch what confuses real users and route it through the backlog, not straight into the code.

## Versioning, simplified

Tag releases only if someone besides you depends on the app. Otherwise, the deploy history is the version history, and that is fine.
