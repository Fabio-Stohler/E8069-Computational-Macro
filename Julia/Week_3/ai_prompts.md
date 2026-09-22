# Session 3: one task, three prompts

Open your own AI assistant (any will do) and use a **new chat** for each prompt, so that the
assistant does not carry context from one prompt to the next. About 10 minutes.

## Prompt 1: vague

```
Write a function that interpolates.
```

Look at the answer before you move on. Which language did it pick? Which method? What does it do
outside the grid? None of this was your decision.

## Prompt 2: context, interface, constraints

Replace `[Julia/Python]` by your language.

```
I solve a growth model by value function iteration in [Julia/Python]. Write
lin_interp(xgrid, fgrid, x): linear interpolation of the values fgrid on the sorted nodes xgrid
at a number x. No packages. First locate the left neighbour, then compute the weight. Say what
happens for x outside the grid.
```

Compare with your own `lin_interp` from part 2 of the notebook. Same structure? Same behaviour
outside the grid?

## Prompt 3: let it explain and test your code

Paste your own function where it says so.

```
Here is my function from class:

[paste your lin_interp]

Explain line by line what it does. Then write five tests, including edge cases, and tell me
which results might surprise me.
```

**Run the tests**, do not just read them. Then discuss with your neighbour:

1. What did prompt 1 decide for you that prompt 2 made you decide yourself?
2. What does *your* function do for `x` below the first or above the last node? Did you know
   before the assistant told you? Is that behaviour what you want inside `vfi_update`, and why
   does it never matter there?
3. Did the assistant get a test wrong? How would you have noticed without running it?

## Three habits

* **Specify** like you would for a coauthor: model, language, interface, constraints.
* **Ask for tests and run them.** Edge cases, a known closed form, a second method.
* **Ask for explanations**, of code you did not write and of code you did. If you cannot follow
  the explanation, the code does not go into your submission.

Course policy: AI assistants are allowed on problem sets and the final project. Document the use
briefly, and be able to explain every part of your submission. The midterm is written without AI
tools.

## Free, self-paced courses, about an hour each

Anthropic:

1. AI Fluency for Students: https://anthropic.skilljar.com/ai-fluency-for-students
2. Claude 101: https://anthropic.skilljar.com/claude-101
3. Claude Code 101: https://anthropic.skilljar.com/claude-code-101

OpenAI Academy, a parallel route and not a one-to-one match:

4. AI Foundations: https://academy.openai.com/public/courses/ai-foundations-juzjs
5. Applied AI Foundations: https://academy.openai.com/public/courses/applied-ai-foundations-hgk7r
6. Agents and Workflows: https://academy.openai.com/public/courses/agents-and-workflows-bieml

These tools help most when you can still tell a good answer from a merely plausible one. Use them
to get further into a problem, not to skip past it.
