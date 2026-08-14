# Decisions Log

**Purpose:** Append-only record of settled choices. Its job is to stop the same question being reopened weeks later, by you or by the AI. Of everything in this kit, this doc earns its keep fastest.

**Rules:**

- Append only. Never edit or delete past entries. If a decision changes, add a new entry that supersedes the old one and says why.
- One line of reasoning per entry. Enough to remember why, not a essay.
- The AI does not reopen anything recorded here. If new information genuinely changes a settled decision, it says so explicitly and asks first.

**Format:**

```
## YYYY-MM-DD: Decision in one line
Reasoning in one or two lines. Supersedes [earlier entry] if applicable.
```

---

<!-- Entries begin here. The six settle-first decisions from the project charter should be the first entries. -->

## 2026-08-14: Objective is a single-page canonical-event-block tool for webinar promo assets
One source block per webinar, six generated channel blocks. Single user.

## 2026-08-14: Definition of done for v1 is the five charter success criteria
Out-of-scope list in the charter is enforced; nothing on it ships in v1.

## 2026-08-14: Deploy target is Vercel with auto-deploy from main
One-click rollback and zero-config static hosting; decided first because it constrains everything else.

## 2026-08-14: Data layer is browser localStorage, no database
Nothing in v1 needs server-side state; a database would be speculative.

## 2026-08-14: No auth
Public marketing text stored client-side; nothing to protect behind an account.

## 2026-08-14: Lifespan is maintained personal tool
Used every webinar cycle, so it gets the full kit ceremony, scaled to low risk.

## 2026-08-14: Risk is internet-exposed, single user, no sensitive data
Security checklist runs before the URL is shared; no auth testing needed since there is no auth.

## 2026-08-14: Stack is static HTML, CSS, and vanilla JavaScript with no build step and no dependencies
Nothing in v1 needs a framework; zero dependencies keeps the audit surface empty. Note: the seven settle-first questions do not cover stack; recorded here so it stays settled.

## 2026-08-14: Instant rollback is available
Vercel Deployments list, previous deployment, Promote to Production. Steps confirmed before they are needed.

## 2026-08-14: Persistent data is client-side only
Rollback is just redeploying. Caution: localStorage does not roll back with the code, so new code must read or migrate any older stored event shape.
