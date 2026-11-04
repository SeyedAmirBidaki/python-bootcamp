# Week 0: Git and GitHub from zero

You have never used a terminal or Git. By the end of this file you will have
installed Git, made a repository, committed to it, pushed it to GitHub,
created a branch, opened a pull request, and fixed the five errors that
everybody hits in their first month.

**Time:** 5 to 7 hours, spread over two or three days. Do not rush it. The
rest of the course assumes you can do everything in the last section from
memory.

There is no AI on this page. Everything here is a command you type and a
result you read, which is the right way to learn a tool this basic. If you get
stuck, the error sections at the end cover most of what can go wrong.

---

## Part 1: the terminal

A terminal is a window where you type commands as text instead of clicking.
That is all it is. It is faster than clicking for almost everything a
developer does, and it is the same on every machine, which is why it is worth
the first hour being slightly uncomfortable.

**Open it:**

- macOS: `Terminal` from Applications, or search for it
- Windows: use **Git Bash**, which you get with Git in part 2. Do not use
  Command Prompt or PowerShell for this course; the commands differ.
- Linux: `Ctrl+Alt+T`, usually

You will see a prompt ending in `$` or `%` or `>`. That means it is waiting for
you.

**Four commands to start with:**

```
pwd                 show the folder you are in ("print working directory")
ls                  list what is in this folder
cd foldername       go into a folder
cd ..               go up one folder
```

Try them. `cd` with no argument takes you to your home folder. Typing `cd ` and
then pressing Tab will complete a folder name, which saves a lot of typing and
a lot of typos.

One thing that surprises everybody: **nothing happens when a command works.**
No "success" message, no popup. Silence means it worked. Developers read
silence as success and text as a problem to solve, and that takes about a week
to get used to.

**Paths, briefly.** `/` at the start means "from the root of the disk".
`~` means your home folder. `..` means the folder above this one. `.` means
this folder. Everything else is relative to where you are, which is why `pwd`
matters more than it looks.

---

## Part 2: install Git and tell it who you are

**Check whether you already have it:**

```
git --version
```

If that prints something like `git version 2.40.1`, skip to the configuration
below.

**If not, install it:**

- **Windows:** download from git-scm.com and install with all the defaults.
  This also gives you Git Bash, which is the terminal you should use.
- **macOS:** run `git --version`; macOS offers to install the command line
  tools for you. Accept it. If it does not offer, `brew install git` if you
  have Homebrew.
- **Linux, Debian or Ubuntu:** `sudo apt install git`
- **Linux, Fedora:** `sudo dnf install git`

Then close and reopen your terminal, and check `git --version` again.

**Tell Git who you are.** Every commit carries a name and an email. These
appear in the history forever, so use the email you want associated with your
work:

```
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Use the same email you will use for GitHub; otherwise your commits will not be
linked to your account and your contribution graph will look empty, which is
confusing for weeks.

Two more settings that make life easier:

```
git config --global init.defaultBranch main
git config --global pull.rebase false
```

The first makes new repositories start on `main` instead of `master`. The
second avoids a warning message you would otherwise meet later.

Check it took:

```
git config --list
```

---

## Part 3: the mental model

Before any commands, four ideas. Read them twice; the commands are easy once
these are clear and baffling until they are.

Git tracks **versions of files**, and it does so in three places, plus one more
far away:

```
  working directory        staging area           local repository        remote
  (your files as          (what you have          (committed history,     (GitHub)
   they are now)           marked to save)         on your disk)
        |                       |                        |                    |
        |      git add          |       git commit       |      git push      |
        +---------------------->+----------------------->+------------------->+
        |                                               |                    |
        |<----------------------------------------------+<-------------------+
                      git checkout / git restore                git pull
```

- **Working directory:** the actual files. Edit them however you like; Git does
  not care until you say so.
- **Staging area:** a waiting room. `git add` puts a file in it. You choose
  exactly what goes into the next commit, which is why you can make three
  unrelated changes and commit them as three separate commits.
- **Local repository:** the saved history, on your machine. `git commit` moves
  what is staged into here, with a message and a timestamp.
- **Remote:** a copy on a server, in this course GitHub. `git push` sends your
  commits there; `git pull` brings other people's down.

The single most useful sentence: **a commit is a snapshot of your whole
project at one moment, with a message saying why.** Not a diff, not a patch; a
snapshot. The diffs you see are computed by comparing snapshots.

The second most useful: **branches are just labels on commits.** Creating a
branch costs nothing, copies nothing, and breaks nothing. That is why
developers make them for everything.

---

## Part 4: your first repository

A **repository** (repo) is a folder that Git is tracking. Let us make one.

```
cd ~
mkdir git-practice
cd git-practice
git init
```

`git init` prints something about an empty repository. Now Git is watching this
folder. Check the state any time with:

```
git status
```

It will say you are on branch `main` with nothing to commit. That is what a
clean repository looks like.

**Make a file and stage it:**

```
echo "# My practice repo" > README.md
git status
```

Now `README.md` appears in red under "Untracked files". Red means "Git sees
this but is not tracking it". Add it:

```
git add README.md
git status
```

It is now green under "Changes to be committed". Green means staged.

**Commit it:**

```
git commit -m "add readme"
```

`-m` is the message. Without it, Git opens a text editor, which is a
disorienting experience the first time; always use `-m`.

Check the history:

```
git log --oneline
```

One line, a short hash, and your message. That hash is the commit's name. You
will use it to refer to this exact snapshot later.

**A good commit message** completes the sentence "this commit will...". So:
"add readme", "fix the empty list crash", "rename tidy.py to sorter.py".
Present tense, lowercase, short. Not "added some stuff" and not "final version
2 real final". You will read these in six months and you will not remember
what you meant.

**Now make a change and see a diff:**

```
echo "A line I just added." >> README.md
git diff
```

`git diff` shows unstaged changes: lines with `-` were removed, lines with `+`
were added. This is the command you will use most often for the rest of your
career. Read it before every commit.

```
git add README.md
git commit -m "add a line to the readme"
git log --oneline
```

Two commits. Notice that `git status` is clean again.

---

## Part 5: GitHub and your first push

GitHub is a website that hosts Git repositories. Git is the tool; GitHub is one
place to keep the copies. You could use Git entirely offline, and the course
would still work, but the sharing and reviewing is what makes it useful.

**Create an account** at github.com if you do not have one. Use the same email
as your Git config. Choose a username you would be happy to put on a CV; it
will be in every repository URL you share.

**Create an empty repository.** Click the `+` in the top right, "New
repository". Name it `git-practice`. **Do not** tick "Add a README"; you
already have one, and a second one will cause a conflict on your first push.
Leave it completely empty. Create it.

GitHub then shows you commands. Use the ones under "…or push an existing
repository from the command line", which look like this, with your username:

```
git remote add origin https://github.com/YOUR-USERNAME/git-practice.git
git branch -M main
git push -u origin main
```

What each does:

- `git remote add origin <url>` — remembers a remote called `origin` at that
  address. `origin` is just a name; it is the conventional one for "the main
  place this lives".
- `git branch -M main` — renames your current branch to `main`, in case it was
  created as `master`.
- `git push -u origin main` — sends your `main` branch to `origin`, and `-u`
  remembers that this local branch follows that remote one, so `git push` on
  its own works from now on.

**Authentication.** GitHub will not accept your password for `git push` any
more. It wants a **personal access token** instead:

1. GitHub, Settings, Developer settings, Personal access tokens, Tokens
   (classic), Generate new token.
2. Give it a note like "laptop git", an expiry of 90 days, and tick the `repo`
   scope.
3. Copy the token. **You will not see it again.** Paste it somewhere safe for
   the next few minutes.
4. When `git push` asks for a password, paste the token. When it asks for a
   username, your GitHub username.

Better: install the GitHub CLI (`gh`) and run `gh auth login`, which handles
this for you and is what most developers use now. If `gh` is available on your
machine, prefer it. Otherwise the token is fine; the token is not a password
and does not give access to your account, only to the repositories you ticked.

Check that it worked:

```
git log --oneline
git status
```

`git status` should say your branch is up to date with `origin/main`. Reload
GitHub in the browser and your README is there.

---

## Part 6: branches and a pull request

A **branch** is a line of work. The point of one is that `main` stays working
while you try something.

```
git switch -c week-1
```

`-c` means create. You are now on a branch called `week-1`, and it starts from
exactly where `main` is. Nothing was copied; the label just moved.

Make a change that is "week 1 work":

```
mkdir week-1
echo "exercise answers go here" > week-1/notes.md
git status
git add week-1/notes.md
git commit -m "start week 1 notes"
git push -u origin week-1
```

Notice the last command names `week-1`, not `main`. You are pushing the branch
you are on, to a branch of the same name on GitHub.

**Open a pull request.** Go to the repository on GitHub. There will be a
yellow banner offering to compare and pull request for `week-1`. Click it.
Write a title ("Week 1 notes") and a description, then "Create pull request".

A **pull request** (PR) is a proposal to merge one branch into another, with a
place to discuss it. Even with nobody else on the project, it is worth opening
one for each week: it gives you a single page showing every change you made,
which is the best way to review your own work. Your brother will review there.

On the PR page, click the "Files changed" tab. That is the diff of the whole
branch against `main`, which is the single most useful view in GitHub.

**Merge it**, when you are happy, with "Merge pull request". Then locally:

```
git switch main
git pull
git log --oneline
```

`main` now contains your work. `git pull` brought the merge down. Delete the
branch if you like:

```
git branch -d week-1
```

Everything is preserved; the label is gone, the commits are on `main`. This is
the loop you will repeat every week, and eventually every day.

---

## Part 7: `.gitignore`, and the file you must never commit

Some files should never go into a repository: virtual environments (thousands
of files, specific to your machine), secrets and passwords, and generated
output.

Create a file called `.gitignore` in the root of your repository with these
lines:

```
.venv/
venv/
__pycache__/
*.pyc
.env
.DS_Store
```

Each line is a pattern. `.venv/` ignores the whole folder and everything in it.
`*.pyc` ignores compiled Python files wherever they are. `.env` is where
passwords and API keys go, and it must never be committed; if you ever commit a
key, consider it public and revoke it, because deleting the file in a later
commit does not remove it from the history.

Check what is ignored with `git status --ignored`. If a folder you expected to
be ignored appears as untracked, the pattern is wrong; a trailing slash means
"folder only" and a missing leading slash means "anywhere".

---

## Part 8: the five errors everybody hits

Read these now, and come back when one of them happens. Recognising the message
is most of the fix.

### 1. Authentication failed, or it keeps asking for a password

```
remote: Support for password authentication was removed
fatal: Authentication failed for 'https://github.com/...'
```

Passwords do not work for `git push`. Use a personal access token in place of
the password, or run `gh auth login`. If you already stored a wrong password in
your system keychain, Git will keep offering it. On macOS:

```
git config --global credential.helper osxkeychain
git credential-osxkeychain erase
host=github.com
protocol=https
```

(type that second command, then press Enter twice). On Windows, Credential
Manager, find `git:https://github.com`, remove it. Then push again and enter the
token.

### 2. "Not a git repository", or you committed to the wrong folder

```
fatal: not a git repository (or any of the parent directories): .git
```

You are in a folder that Git is not tracking. Either you are in the wrong
place (`pwd` and `ls` to check) or you never ran `git init` there. The common
version of this mistake is running `git init` in your home folder and then
committing your entire life; if you have done that, delete the `.git` folder
you just made (`rm -rf .git` in that folder, being very sure of `pwd` first)
and start again inside the project folder.

### 3. A merge conflict

```
CONFLICT (content): Merge conflict in app.py
Automatic merge failed; fix conflicts and then commit the result.
```

Two branches changed the same lines. Git cannot guess which you want, so it
writes both into the file:

```
<<<<<<< HEAD
total = 0
=======
total = 100
>>>>>>> week-1
```

Open the file. Delete the `<<<<<<<`, `=======` and `>>>>>>>` lines, and edit
the code so it is what you actually want. It may be one side, the other, or a
combination that is neither. Then:

```
git add app.py
git commit
```

That commit completes the merge. The mistake people make is deleting the
markers without deciding, which leaves code that runs but is wrong. Read both
versions properly; a conflict is Git telling you that two people's intentions
disagreed, and only you know what the program should do.

To avoid most of them: pull before you start work, keep branches short, and
commit often.

### 4. Detached HEAD

```
You are in 'detached HEAD' state.
```

You are looking at a commit that is not the tip of any branch, usually because
you ran `git checkout <hash>` or `git checkout v1.0`. You can look around and
run the code, but new commits here belong to no branch and are easy to lose.

The fix is almost always:

```
git switch main
```

If you made commits while detached and want to keep them:

```
git switch -c rescue
```

That creates a branch at your current position, so the commits have a home.
Then merge or cherry-pick as you like. Nothing is lost until Git's cleanup runs
weeks later, so do not panic.

### 5. You pushed to main by mistake

You meant to push a branch, and you pushed straight to `main`. What to do
depends on whether anyone else has it.

**Nobody else, and you have not shared it:** undo the commit locally and force
the push.

```
git log --oneline          # find the commit before your mistake
git reset --hard <hash>    # move main back; your working files change too
git push --force origin main
```

`--force` rewrites history on the remote. Only ever do this on a branch nobody
else has, and never on `main` of a shared repository. If you are unsure, do not
force; ask.

**Somebody else might have pulled it:** do not rewrite history. Instead, revert
it, which makes a new commit that undoes the old one:

```
git revert <hash>
git push
```

The change is still in the history, which is honest, and the code is correct
again. On any shared project, `revert` is the answer and `reset --hard` is not.

If you only committed to main locally and have not pushed:

```
git switch -c week-1        # take the commits to a new branch
git switch main
git reset --hard origin/main # put main back where the remote has it
```

Now your work is on `week-1` and `main` matches the server, which is what you
wanted in the first place.

---

## Part 9: the three drills

Do these before week 1. They are not optional and they are not a formality:
each one exercises something the course needs you to be able to do without
thinking about it.

Use your `git-practice` repository, or the real course repository if your
brother has already made it. Wherever the commands say `YOUR-USERNAME`, use
yours.

### Drill 1: a branch with your name in it

Goal: create a branch, add a file, commit, push, and see it on GitHub.

```
git switch main
git pull
git switch -c drill-1
mkdir drills
```

Create `drills/name.md` with these four lines, filled in:

```
Name:
Date:
One thing I already know about Git:
One thing I am not sure about:
```

Then:

```
git add drills/name.md
git commit -m "drill 1: my name"
git push -u origin drill-1
```

Open GitHub, find the branch, and confirm the file is there and the text is
right. If the text is wrong, edit the file, `git add`, `git commit -m "fix
typo"`, `git push`, and look again. That loop is the whole job.

### Drill 2: an edit and a diff, read properly

Goal: make a change, and read the diff before committing it.

On the `drill-1` branch, add three more lines to `drills/name.md`: what you did
in the last hour, one command you now understand, and one you do not.

```
git diff
```

Read it. You should see three `+` lines and nothing else. If you see more, you
have changed something you did not mean to; that is exactly why you read the
diff.

```
git add drills/name.md
git commit -m "drill 2: three more lines"
git push
```

Note that `git push` without arguments worked, because `-u` remembered the
upstream branch.

### Drill 3: a pull request, reviewed and merged

Goal: the full loop, from branch to merged.

```
git switch main
git pull
git switch -c drill-3
```

Create `drills/commands.md` listing at least eight of the Git commands you
have used so far, one per line, each followed by a dash and one sentence saying what it
does. Write the sentences yourself; if you cannot, look the command up and
then write it from memory.

```
git add drills/commands.md
git commit -m "drill 3: commands I know"
git push -u origin drill-3
```

Open the pull request on GitHub. In the description, answer in three lines:
which command you found hardest, which one you would explain to a friend
tomorrow, and what still feels like magic. Then merge it, and locally:

```
git switch main
git pull
git log --oneline --graph
```

`--graph` draws the branch structure as text. Look at it; this is what all
those diagrams in tutorials are showing.

**You are done with week 0 when** all three drills are merged into `main` and
you can do drill 1 again from memory, without looking at this page. That is
fifteen minutes of typing and it is the difference between knowing about
branches and being able to use them.

---

## A short reference

Keep this somewhere; you will need it less often than you think and more often
than you expect.

```
git status                     what is staged, what is changed, what is untracked
git diff                       unstaged changes
git diff --staged              staged changes, about to be committed
git add FILE                   stage a file (git add . stages everything here)
git commit -m "message"        snapshot what is staged
git log --oneline --graph      the history, drawn
git switch BRANCH              change branch
git switch -c BRANCH           create and switch
git push                       send commits to the remote
git pull                       fetch and merge from the remote
git restore FILE               throw away unstaged changes to a file
git restore --staged FILE      unstage, keep the changes
git remote -v                  where this repository points
```

`git restore FILE` throws away your edits and cannot be undone. It is the one
command in this list that destroys work, so read it twice before typing it.

---

## What you can do now

If you worked through this page, you can: open a terminal and move around it,
make and commit changes, push to GitHub, work on a branch, open and merge a
pull request, read a diff, and fix the five errors that stop beginners. That is
more Git than many working developers use in a normal week, and it is all the
course needs.

Go to `week-1-foundations/README.md`. The first thing to do there is make your
`week-1` branch.
