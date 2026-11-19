---
title: 'Prompt Engineering for Developers: How to get better results from AI'
date: '2026-11-19T09:00:00.000Z'
slug: 'prompt-engineering-for-developers-how-to-get-better-results-from-ai'
description: 'AI coding assistants are only as good as the instructions you give them.
Here is how to write prompts that actually work.'
author:
  name: Darius Kletter
tags:
  - ai
  - prompt-engineering
  - llm
  - productivity
---

AI assistants have become part of my daily work as a software engineer. They
write tests, explain legacy code, draft documentation and sometimes even find
the bug I have been staring at for an hour.

But the results vary _a lot_.

Sometimes the answer is spot on. Sometimes it is confidently wrong, way too
generic or solves a completely different problem.

Most of the time, the difference is not the model. **It is the prompt.**

## The Problem (What usually goes wrong)

```text
Write a function to validate a form.
```

**Issues:**

- ❌ Which language? Which framework?
- ❌ Which fields? Which rules?
- ❌ What should happen on error?
- ❌ What does "good" even look like here?

The model has to guess all of this. And when a model guesses, you get the most
average answer possible — which is rarely the one you need.

Think of it like this: you are briefing a very smart colleague who just joined
the team today. They know a lot, but they know **nothing** about your project.

## The Solution: Give context, be specific, show the goal

### 1️⃣ Provide context

Tell the model what you are working with and why.

```text
I am working on a React 19 app with TypeScript, react-hook-form and Yup.
Validation messages are translated globally via i18next and yup.setLocale,
so schemas should not contain any message strings.
```

Context is the single biggest lever. The more the model knows about your
environment, constraints and conventions, the less it has to invent.

### 2️⃣ Be specific about the task

Describe exactly what you want — including the edge cases.

```text
Write a Yup schema for a registration form with:
- email: required, valid email
- password: required, min 8 characters, at least one number
- confirmPassword: must match password
- age: optional, integer, min 18 if provided
```

Vague input → vague output. Precise input → precise output.

### 3️⃣ Define the output format

If you want only code, say so. If you want a table, a list or JSON, say so.

```text
Return only the TypeScript code in a single code block.
No explanation, no example usage.
```

This saves you from scrolling through three paragraphs of introduction to find
the five lines you actually needed.

### 4️⃣ Show examples (few-shot prompting)

Examples are often more powerful than descriptions. Show the model one or two
cases of what you expect and it will pick up the pattern.

```text
Convert these commit messages to the Conventional Commits format.

Example:
Input: "fixed the linkedin link"
Output: "fix: linkedin link"

Input: "added new blog post about prompts"
Output:
```

The model now knows the style, the tone and the format — without you having to
explain any of it.

### 5️⃣ Let the model think step by step

For complex problems like debugging or architecture decisions, ask the model to
reason before answering.

```text
Here is a failing test and the component it tests.
First explain step by step what the test expects and what the component
actually does. Then identify the root cause. Only then suggest a fix.
```

Forcing the reasoning first leads to noticeably better answers than jumping
straight to "here is the fix".

### 6️⃣ Iterate

Your first prompt does not have to be perfect. Treat it like a conversation:

- "Make it shorter."
- "Use `zod` instead of `yup`."
- "This breaks when the list is empty — handle that case."

Good prompting is a feedback loop, not a single shot.

## The Result: A prompt that actually works

Putting it all together:

```text
Context:
I am working on a React 19 app with TypeScript, react-hook-form and Yup.
Validation messages are handled globally via yup.setLocale and i18next,
so schemas must not contain any message strings.

Task:
Write a Yup schema for a registration form with:
- email: required, valid email
- password: required, min 8 characters, at least one number
- confirmPassword: must match password
- age: optional, integer, min 18 if provided

Also export the inferred TypeScript type for the form values.

Output:
Return only the TypeScript code in a single code block.
```

Compare that to "Write a function to validate a form." Same model, completely
different result.

## Common mistakes to avoid

- 🚫 **Assuming the model knows your codebase** – it does not, unless you show
  it.
- 🚫 **Asking multiple unrelated things at once** – split them into separate
  prompts.
- 🚫 **Only saying what not to do** – tell it what to do instead.
- 🚫 **Blindly trusting the output** – always review, test and understand the
  code before you commit it.

## Benefits

- ✅ **More accurate** answers on the first try
- ✅ **Less back and forth** with the AI
- ✅ **Code that fits your project** and conventions
- ✅ **Reusable prompts** you can share with your team
- ✅ **Better understanding** of your own problem — writing a clear prompt
  forces you to think it through

## Takeaway

Prompt engineering is not magic and it is not about secret keywords.

It is about **clear communication**: give context, be specific, define the
output and show examples.

Funny enough, these are exactly the same skills that make you a better
engineer when writing tickets, reviewing PRs or explaining a problem to a
colleague.

The better you explain what you want, the better the result — whether you are
talking to a human or a machine.
