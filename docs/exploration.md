# Exploration

**Purpose:** The phase before the project exists. This is the only doc in the kit addressed to you rather than to the AI, and nothing in it gets filled in. It is a method for the throwaway chats where an idea proves it deserves a repo, or dies cheaply. Most ideas should die here, and killing an idea in a free chat is the cheapest engineering you will ever do.

Do this in a plain chat. No repo, no files, no commitment. Everything in this phase is disposable, which is exactly what makes it useful: you can be wrong at zero cost.

---

## Start the chat

Describe the problem in four parts before you describe any solution:

> I keep running into this problem: [what is slow, repetitive, or error-prone]. I'm thinking about an app that takes [inputs] and does [process] to produce [output], so that [goal]. Help me think it through before we build anything.

If you cannot fill in the first bracket with something real, you have a solution looking for a problem. That is worth knowing now.

## The moves

Use the ones the conversation needs. A simple idea might take one, a complicated one all four.

**Let it interview you.**

> Interview me one question at a time to understand this problem fully. Ask about details, rules, and edge cases I haven't mentioned.

**Hunt for weak spots.**

> Name three specific situations where this app would give a wrong, confusing, or useless result.

**Cut until it hurts.**

> Describe the simplest version that still solves the core problem. What am I including that v1 does not need?

**Throw away a prototype.** Ask for a quick mockup or working artifact right in the chat and poke at it. You are not building the app; you are finding out whether the idea survives contact with a screen. Expect to discard it. If discarding it stings, that is data for the next section.

## The graduation test

An idea earns a repo when most of these are true:

- You can state the problem in one sentence and name a real person who has it, even if that person is you.
- You would use the thing next week even if it stayed ugly.
- The throwaway prototype made you want to keep it.
- The chat has started accumulating decisions you are afraid of losing.

That last one is the tell. When the chat becomes something you are scared to close, the idea has outgrown the chat.

If the idea fails the test, close the chat and feel good about it. You spent an hour instead of a month.

## The handoff

When an idea graduates, do not rebuild the thinking from memory. Run this at the end of the exploration chat:

> This idea has earned a real project. Distill this whole conversation into charter inputs I can carry into a new repo: the problem in one sentence and who has it; inputs, process, output, and goal; success criteria for v1; everything we decided to cut, as an out-of-scope list; any of these we already settled: objective, definition of done, deploy target, data layer, auth, lifespan; and the open questions the project charter interview should resolve. Plain markdown, no code.

Save the output. Then clone this kit as your new project and run the bootstrap prompt in the README, which will ask for these notes and feed them into the charter interview. Exploration output becomes charter input, and nothing gets re-derived.
