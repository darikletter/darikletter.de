---
title: 'What to set up before you start a new project with AI'
date: '2026-11-27T09:00:00.000Z'
slug: 'what-to-set-up-before-you-start-a-new-project-with-ai'
description: 'Five things to have in place from day one, so your AI agent
produces code you actually want to keep.'
author:
  name: Darius Kletter
tags:
  - ai
  - tooling
  - productivity
---

AI agents are fast. That's great, but it also means they produce a lot of code
in very little time. Without guardrails, that code drifts in style, breaks
silently and ignores how you like to work.

So before you write the first prompt, put these five things in place. You don't
have to do it alone: the agent can set most of it up with you.

## 1. ESLint, configured your way

Linting is the cheapest way to tell an agent what "good code" means in your
project. Set up the rules that match your code style and let the agent run the
linter after every change. It will fix its own mistakes before you even see
them.

## 2. Prettier

Don't spend a single review comment on formatting. Add Prettier, format on save
and on commit, and the question is settled for you and the agent.

## 3. A test framework

Tests are how the agent knows it's done, and how you know it didn't break
anything. A setup that works well for React projects:

- **Vitest** with **React Testing Library** for unit and component tests
- **Playwright** for end-to-end tests

Have it in place from the start, so every feature comes with tests instead of
"we'll add them later".

## 4. Helpful MCP servers

MCP servers give your agent access to tools and information it doesn't have on
its own. A good first one is [Context7](https://context7.com/), which gives the
agent up-to-date documentation instead of whatever it remembers from training.
No more hallucinated APIs from three versions ago.

## 5. Skills for planning and executing work

Skills are reusable instructions that teach the agent a workflow. I use
[Matt Pocock's skills](https://github.com/mattpocock/skills) to plan and execute
work in a structured way, from grilling a plan to test-driven development.

### Tip: plan ahead

Plan the whole project, maybe even your complete v1, together with the agent
and split it into tickets.

Why? The agent will finish the first draft very quickly, and after that it just
waits for your next idea. You might as well plan ahead. Once you approve the
first proof of concept, hand it a big pile of well-defined tickets and let it
work.

## Wrap-up

None of this is new. It's what a good project setup always looked like. The
difference is that with AI, the payoff is much bigger: the agent follows these
guardrails every time, at a speed no human can match. Set them up once and
every line it writes gets better.
