# UI/UX Guidelines

## Overall feel

Dense and utilitarian, built for someone who uses it every webinar cycle. Fast over pretty. Desktop only; this is a work tool used at a desk.

## Visual style

Light mode. Neutral grays with a single blue accent. System font stack, no webfonts. No gradients, no purple, nothing that looks like a startup landing page. Generated blocks render in a monospace font so pasted output is predictable.

## Layout and navigation

One page. Event form on the left, generated channel blocks on the right, stacked vertically when the window is narrow. The primary action is the Copy button on each block. No navigation, no routes, no modals.

## Copy and tone

Labels match the canonical block field names exactly: Title, Description, Date, Time, Time zone, Speakers, Registration link, Broadcast link, Recording link, Call to action. Empty states say what to do next in one sentence. Errors say what happened and what to do, in plain language. The app never uses marketing voice on itself.

## Interaction states and accessibility

Every interactive element ships with all of its states: default, hover, focus, disabled, loading, empty, and error. A screen with only the happy state built is not done.

Baseline accessibility, always on: real labels on form fields, visible focus indicators, every action reachable by keyboard, alt text on meaningful images, and color contrast that passes without squinting.

## Defaults the AI should follow

- Approved patterns get reused, not redesigned. Once a form layout, table style, or button treatment is approved on one screen, every later screen uses it. If a pattern is not working, propose a change to the pattern itself rather than quietly diverging on one screen.
- Reuse existing components and styles before inventing new ones.
- One new screen at a time, reviewed before the next.
- When a design choice is ambiguous, pick the simpler option and flag it, rather than adding flourishes.
- Copy buttons confirm visually that the copy happened; that is the whole feedback loop of this app.
