# UI/UX Guidelines

**Purpose:** Your design preferences, stated once. Without this doc, every screen gets invented fresh, each in a slightly different style, and you spend your sessions correcting the same instincts repeatedly. With it, the AI's first draft of any screen starts close to what you wanted.

**Interview prompt.** Paste this into your AI tool:

> Interview me one question at a time to write my UI/UX guidelines. Ask about: overall feel (dense and utilitarian versus spacious and polished), color preferences and anything I dislike, light or dark mode, typography preferences if any, how much the app should explain itself on screen, mobile versus desktop priority, and accessibility requirements. If I have screenshots of apps whose look I like, ask me to share them and describe what specifically to take from each. Then draft the doc.

---

## Overall feel

<!-- Two or three sentences. "Dense, fast, keyboard-friendly, built for someone who uses it daily" and "clean and self-explanatory for people who open it once a month" lead to different apps. -->

## Visual style

<!-- Colors, mode, typography, spacing. Name apps you want it to feel like. Also name what you dislike; "no gradients, no purple, nothing that looks like a crypto landing page" is actionable. -->

## Layout and navigation

<!-- Single page or multiple views. Where the primary action lives. Mobile-first, desktop-first, or desktop-only. -->

## Copy and tone

<!-- How the app talks: labels, empty states, errors. Plain language rules. Anything it should never say. -->

## Interaction states and accessibility

Every interactive element ships with all of its states: default, hover, focus, disabled, loading, empty, and error. A screen with only the happy state built is not done.

Baseline accessibility, always on: real labels on form fields, visible focus indicators, every action reachable by keyboard, alt text on meaningful images, and color contrast that passes without squinting. Add stricter requirements here if you have them.

## Defaults the AI should follow

- Approved patterns get reused, not redesigned. Once a form layout, table style, or button treatment is approved on one screen, every later screen uses it. If a pattern is not working, propose a change to the pattern itself rather than quietly diverging on one screen.
- Reuse existing components and styles before inventing new ones.
- One new screen at a time, reviewed before the next.
- When a design choice is ambiguous, pick the simpler option and flag it, rather than adding flourishes.
<!-- Add your own. -->
