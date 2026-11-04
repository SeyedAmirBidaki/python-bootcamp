# The rules of engagement

Read this once at the start, and skim it again at the start of each week. It
is about six minutes of reading and it decides whether the course works.

Two tracks, two sets of rules. The reason they are different is simple: the
exercises exist to find out what you know, and the projects exist to teach you
how to work with an AI. Using AI on the first defeats the purpose; refusing to
use it on the second leaves you unprepared for how the work is actually done.

---

## Track A: no AI at all

Applies to every `exercises.md`, every quiz, and the `plan.md` part of a
project (the planning is yours; see below for the rest).

**What is allowed:**

- `python3` itself, both the interactive shell and running files
- the official Python documentation at docs.python.org
- `help()` in the shell, for example `help(str.split)`
- error messages, read carefully
- the hints file, one hint at a time, after real effort
- paper, a pen, and your own notes from previous weeks
- asking a search engine a *definition* question, like "what does
  dict.get return when the key is missing"

**What is not allowed:**

- any AI chat, in any window, including on your phone
- AI autocomplete in your editor, if you have it installed for the projects
- asking a person to write the code for you
- copying a solution from the internet, a tutorial, or a previous exercise
  written by somebody else
- reading the solutions folder, however tempting

**The grey areas, and how to settle them:**

*Typing a definition question into a search engine is fine; pasting the whole
exercise in is not.* The line is whether you are looking up a fact about the
language or asking for the answer to the problem. "What is the difference
between a list and a tuple" is a fact. "How do I count words in a string"
while the exercise is "count the words in a string" is the answer.

*Copying a pattern from the docs is fine.* The docs show `" ".join(words)` as
an example of `str.join`. Using that in your solution is exactly what the docs
are for. Copying an entire working function from a tutorial that solves the
same exercise is not.

*Asking a friend what an error means is fine.* Asking a friend to look at your
code and tell you what is wrong is not, for Track A. In Track B it is fine,
because the whole point there is learning how to read and fix.

If you are unsure, ask yourself one question: *after this, could I write the
same thing again tomorrow with nothing in front of me?* If yes, you have
learned something. If no, you have borrowed something, and the borrowing will
be visible in week 2 when the material builds on it.

**Why the rule is strict.** It is not moral disapproval of AI. It is that the
exercises are a measurement, and a measurement you have corrupted tells you
nothing. If you use AI and score 10 of 10, your brother will think you are
ready for week 2, and week 2 will be miserable. The score is not the point;
the information is.

---

## The twenty-minute rule

Before you search for anything in Track A, spend twenty minutes on it
yourself. Actually set a timer the first few times; twenty minutes is longer
than it feels.

Use the time like this:

1. Read the error again, out loud.
2. Print the values you think you have, just before the line that fails.
3. Try one different approach, even if you suspect it will not work.
4. Write one sentence describing what you do not understand.

That last step is the useful one. Vague confusion ("it does not work") turns
into a real question ("why is `total` not defined when the list is empty?"),
and a real question is often answered by the act of writing it down. If it is
not, it is now a search that will find something.

The rule is not there to make you suffer. It is there because the twenty
minutes is where most of the learning happens, and it is the part that an AI
removes completely if you let it.

---

## Track B: Cursor, used deliberately

Applies to every `project.md`, and to the code parts of week 4's mini
projects.

**You write:**

- `plan.md`, entirely, before you prompt
- the decisions the brief leaves open (data shapes, rules, edge cases)
- the core logic of the thing being built
- the AI log

**Cursor may write:**

- boilerplate: argument parsing, a Flask route skeleton, a CSV reader
  invocation, a matplotlib incantation
- the thing you already understand but do not remember the exact syntax for
- a first draft of something you will then rewrite
- answers to "why does this do that" questions

**Cursor may not decide:**

- what the program should do
- how the data is structured
- which of two designs to use, unless you have written down why you agree

If you find yourself asking "what should I do next", stop and go back to
`plan.md`. That question is yours. If you find yourself asking "what is the
argument called again", ask away; that is memorisation, and memorising an API
by hand is a waste of your week.

---

## The AI log

Every project needs `ai-log.md`, with at least three entries (four from week
2 onward). Each entry looks like this:

```
### Prompt 2: remove a note by number

What I asked for: a function to delete a note by the number the user typed.
What I got: something that deleted by list index, so typing 1 removed the
second note.
How I noticed: I added three notes, removed number 1, and note 2 vanished.
What I changed: subtracted 1 before indexing, and added a range check.
What I would ask differently: I should have said the number shown to the user
starts at 1. That was the whole bug, and it was my prompt's fault, not the
AI's.
```

Three things to notice about that example. It is specific. It admits the
mistake was partly the prompt's fault. And it says what changed, not just that
something changed.

An entry that says "it worked" is not an entry. Write what you checked and
what you expected to see. If every prompt worked first time, you were not
looking hard enough, and your acceptance checks will show it.

---

## How to ask a good question

Whether you are asking Cursor, a search engine, or your brother, the same four
things make the difference:

1. **What you expected.** "I expected `count_lines` to return 2."
2. **What happened.** "It returned 3."
3. **The exact error, copied, not paraphrased.** If there is no error, say the
   value you got.
4. **What you already tried.** Two sentences is enough, and it stops somebody
   suggesting the first thing you did.

A question without those four gets a generic answer, which is usually the
answer you already had. This is true of AI as much as of people; a vague
prompt gets a vague answer, and then you spend an hour debugging the vagueness.

---

## The honesty pledge

Copy this into the top of each week's `README.md` when you start the week, and
sign it with your initials. It is not legally binding and nobody will check.
It is a reminder, and reminders work.

```
I will do Track A without AI, and I will write down what I actually got,
not what I wish I had got.
I will not read the solutions folder.
I will keep an honest AI log in Track B, including the prompts where the AI
was wrong and the ones where I could not tell.
If I break a rule, I will write it in my README and say which exercise it
affects.
```

That last line is the important one. Breaking a rule and admitting it costs
you one exercise's worth of information. Breaking it and hiding it costs you
the week.

---

## When you are stuck and none of this helps

Two situations where the right move is to stop and ask for help rather than
push on.

**You have been on the same exercise for over an hour** and the twenty-minute
rule is not producing progress. Write down the four question parts, move to the
next exercise, and bring it to your brother at the end of the week. One
unfinished exercise is data. Three days lost to one exercise is a waste.

**You are copying without understanding.** If you notice your hands typing
something you could not explain, stop. Delete it. Go back to the plan. This
applies in both tracks, and it is the single most common way people get
through a course like this without learning anything.

There is no prize for finishing the week. There is a prize for being able to
do the next week.
