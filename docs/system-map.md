# System Map

**Create this doc only when the app gains a database, an external service, or a third component. Before that, the codebase is the map and this file should stay empty or absent.**

**Purpose:** One page that shows what talks to what, so a change in one place stops silently breaking another. It pays for itself the first time a session starts with no memory of how the pieces connect.

**Interview prompt.** Paste this into your AI tool once the trigger above is met:

> Read the codebase and draft docs/system-map.md: every component, every data store, every external service, and what talks to what, including direction. Flag anything that surprised you or that exists but appears unused. Keep it to one page.

---

## Components

<!-- Each moving piece in one line: the web app, the API, the worker. What it does and where it runs. -->

## Data stores

<!-- Each place data persists: database, file storage, caches. What lives in each and which components read and write it. -->

## External services

<!-- Each third-party service: what it is for, which component calls it, whether it costs money, and the name of the environment variable holding its key. Never the value. -->

## Connections

<!-- What talks to what, with direction. "Web app calls API, API reads and writes Postgres, API calls Stripe" beats a diagram nobody updates. -->

## Update rule

Update this doc in the same commit that adds or removes a component, store, or service. A stale map is worse than no map.
