# Python bootcamp: five weeks, two tracks

This is a five-week course for someone who has just finished learning Python
from the very beginning through classes and inheritance, and has not yet
decided what kind of developer to be. It assumes no experience with Git, a
terminal, or an AI editor. It is designed to be worked through alone, at two
or three hours a day, with somebody checking in at the end of each week.

It is not a reference book and it is not a certificate. It is a set of
exercises and projects arranged so that, by the end, you know two things: how
much of Python you actually understand without help, and which of the four
common directions of the job you enjoy.

---

## The idea in one paragraph

Every week has two tracks. **Track A** is exercises you do with no AI at all:
no chat window, no autocomplete, no assistant. Its job is to find out what you
really know. **Track B** is a project you build with Cursor. Its job is
different: breaking a problem down before you prompt, writing a prompt that
constrains the answer, reading the generated code critically, and debugging
it when it is wrong. Most courses do one or the other. Doing both, in the same
week, on the same ideas, is what makes the difference between someone who can
use an AI and someone who is being carried by one.

---

## The roadmap

| Week | Theme | Track A (no AI) | Track B (with Cursor) |
| --- | --- | --- | --- |
| 0 | Git and GitHub from zero | — | Three hands-on drills: branch, commit, push, pull request |
| 1 | Foundations | 10 exercises: strings, lists, dicts, loops, comprehensions | A terminal notes app that saves to a file |
| 2 | Functions and objects | 10 exercises: function design, scope, classes, inheritance | A small library system with classes and a text menu |
| 3 | Files, errors, tests | 10 exercises: files, pathlib, JSON, exceptions, pytest, tracebacks | A CSV cleaner with a test suite |
| 4 | Which direction fits you | — | Two of four small projects: web API, scraper, data analysis, automation |

Each week takes 15 to 20 hours. Five weeks, at that pace, is about 80 hours of
actual work, which is a realistic amount to turn a beginner into somebody who
can build small things unaided.

Week 4 has no Track A. By then the point is not another set of exercises, it is
to build something from a corner of the job and notice how it feels.

---

## How the two tracks work

**Track A, exercises.** No AI, no autocomplete, no copying from a tutorial. You
may use the official Python documentation, error messages, and your own notes.
The exercises are a mix of four kinds:

- *predict the output* — read code and say what it prints, before running it.
  This is the fastest way to find out whether you actually understand a
  construct or just recognise it.
- *find the bug* — working-looking code with one deliberate mistake. You get
  an error message and you have to use it.
- *write a function or class* — from a written specification with example
  cases. The starter file checks your answer, so you know when it is right.
- *explain this code* — write what a piece of code does in your own words. If
  you cannot, you do not understand it yet, and no amount of running it will
  fix that.

Each week's starter file gives you one line of feedback per exercise, PASS or
FAIL, and never shows you the answer. The hints file gives one nudge each, no
solutions. Reference solutions exist, but they are in a folder your brother
keeps, not in your copy.

**Track B, projects.** Cursor is allowed, and used deliberately. The pattern is
the same every week:

1. Write the plan yourself first, in `plan.md`. Break the problem down, decide
   the data shape, decide the open questions the brief leaves to you.
2. Prompt in slices: one function or one behaviour at a time, saying what
   already exists and what you want back.
3. Read the generated code before you paste it. Ask which line does the work,
   what each branch is for, and what breaks if you delete a line.
4. Keep an **AI log**: what you asked, what you got, how you noticed it was
   wrong, what you changed. At least three entries per project, one of which
   must be a genuine AI mistake.
5. Run the acceptance criteria and record the results.

The AI log is not paperwork. It is the only part of a Cursor project that
proves you were driving.

---

## The rules of the game

The full version is in [rules.md](rules.md). The four that matter most:

1. **Twenty minutes of struggle before you search.** Real, timed. Then you may
   look things up.
2. **Track A is closed-book on AI.** Not "I only asked for a hint". Closed.
   If you break it, the exercise stops telling you anything useful, which is
   the actual loss.
3. **In Track B, you must be able to explain every line you keep.** If you
   cannot, delete it and ask again, smaller.
4. **A failing test that describes a real bug is a success.** Hiding it is the
   failure.

---

## How to submit work

Everything lives in one Git repository. Your copy is your own, and you work on
a branch per week:

```
main
├── week-0-git        (drills)
├── week-1            (exercises + notes app)
├── week-2            (exercises + library system)
├── week-3            (exercises + cleaner + tests)
└── week-4            (two mini projects + what-i-learned.md)
```

At the end of each week, push your branch and open a pull request into `main`.
The pull request description is three lines: what it does, what it does not do
yet, and what was hardest. Your brother reviews it there, and the review is a
conversation in the comments rather than a verdict.

If you have never done any of that, week 0 teaches it, from installing Git to
opening your first pull request. Do not skip it because it looks like
plumbing; it is the plumbing you will use every day of your working life.

---

## What to do when you are stuck

In this order. Stop at the first one that works.

1. **Read the error message from the bottom up.** The last line is the
   diagnosis. The line above it names the file, the line number, and the
   expression that broke.
2. **Cut the problem in half.** Print the value you think you have, right
   before the line that fails. Half the time you are wrong about what the
   variable holds.
3. **Twenty minutes of your own effort.** Try two different approaches and
   write down what each one did. This is not wasted time; it is the part that
   teaches you.
4. **The official documentation.** For Python, docs.python.org. For a library,
   its own docs, not a blog post from four years ago.
5. **A search engine**, with the exact error message in quotes.
6. **A hint**, from `hints.md`, one exercise at a time.
7. **Ask your brother**, with four things: what you expected, what happened,
   the exact error, and what you already tried. If you cannot write those four,
   you have not finished steps 1 to 3.

For Track B, there is a separate and legitimate option: ask Cursor. But ask it
a question ("why does this return None when the list is empty?"), not for a
rewrite. A question teaches you something; a rewrite teaches you nothing and
hides the problem.

---

## What you will be able to do at the end

Honestly, not everything. You will not be employable as a developer after five
weeks, and any course that claims otherwise is selling something. What you
will be able to do:

**Write and debug small Python programs alone.** A hundred lines, several
functions, a class or two, reading and writing files, handling the errors that
actually happen. No tutorial open, no assistant.

**Read code you did not write and say what it does.** Including code an AI
generated, which is now a substantial part of the job.

**Use the tools of the trade.** A terminal, a virtual environment, pip, Git,
GitHub, pull requests, pytest, and one AI editor used deliberately rather than
superstitiously.

**Design a small system.** Decide what the classes are, where each rule lives,
and what the data looks like on disk. That is the skill that separates someone
who can follow a tutorial from someone who can build a thing.

**Know which direction you want.** From four real projects in four corners of
the job, and a written note on which one you would do again tomorrow.

**And a realistic sense of what you do not know**, which is the most useful
thing on the list. Everybody at every level has that list. The difference is
whether you know what is on yours.

---

## The files

```
hub/
  README.md            this file
  week-0-git/          Git and GitHub from zero, with three drills
  rules.md             the no-AI rules, in full
week-1-foundations/    exercises, hints, starter file, notes-app project
week-2-functions-and-oop/
week-3-files-errors-tests/
week-4-mini-projects/  four project briefs, pick two
solutions/             for the mentor: reference answers and quizzes
```

Start with `week-0-git/README.md`. Then read `rules.md` once, properly, before
week 1. It is short, and the whole course depends on you actually following it.

---

## One last thing

If a week takes twice as long as the estimate, that is normal and it is not a
sign you are not suited to this. If a whole week feels easy, say so; the
material can be made harder, but a week spent being bored teaches nothing.
Tell your brother which it was. That feedback is worth more than the exercise
scores.
