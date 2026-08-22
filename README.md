# Git Playground

A practice repository for the Coding Club Git session. **Nothing here is a
puzzle.** Break it, mess it up, delete things. It is here to be experimented on.

Everything you do in your own fork is yours alone. You cannot damage this
original copy, and you cannot affect anybody else.

---

## The practice track

Work through these in order. Each one is a command you will need later tonight.

### 1. Fork this repository

Click **Fork**, top right of this page. Not "Use this template" - those are two
different buttons, and the wrong one will cause you problems later.

You now have your own copy at `github.com/<your-username>/git-playground`.

### 2. Clone your fork

```
git clone https://github.com/<your-username>/git-playground.git
cd git-playground
```

Use *your* username, not mine. Everything below runs from inside that folder.

### 3. Look at the history

```
git log
```

Press `q` to get out. That `q` matters - `git log` opens a viewer, and until you
press `q` your terminal will ignore everything you type.

Now the readable version:

```
git log --oneline
```

### 4. Find the other branches

```
git branch -a
```

There is a branch called `experiment` hiding in here. Go and look at it:

```
git checkout experiment
```

Your files just changed on disk. Look in the folder - there is a file here that
does not exist on `main`. Now come back:

```
git checkout main
```

It is gone again. Nothing broke. That is what branches are.

### 5. Read a tag

```
git tag
git tag -n99
```

Tags are labels stuck on a specific commit. `git tag` shows their names,
`git tag -n99` shows the message written on them too.

### 6. Ask who wrote a line

```
git blame recipes/chai.md
```

Every line, and which commit last touched it. It is called blame, but it is just
attribution.

### 7. Compare two points in time

```
git diff v1.0 v2.0
```

Lines starting `-` were removed. Lines starting `+` were added.

### 8. Recover something deleted

Somebody deleted `notes/old-plan.md`. Find the commit that did it:

```
git log --diff-filter=D --name-only
```

Then read the file as it was, one commit *before* it was deleted:

```
git show <commit-hash>^:notes/old-plan.md
```

The `^` means "the commit before this one". Without it you get an error, because
by that commit the file is already gone.

### 9. Make your first pull request

This is the important one. Practise it here so it is boring by the time it counts.

```
git checkout -b my-first-branch
```

Now create a file at `hello/<your-github-username>.md` - the name has to match
your GitHub username. Put anything in it. Say hello, write a joke, whatever.

```
git add hello/
git commit -m "say hello"
git push origin my-first-branch
```

Now go to **your fork** on GitHub. There will be a green **Compare & pull
request** button. Click it.

**Check the box on the left says `satushankar/git-playground` and `main`.** That
is the most common mistake - people open a pull request against their own fork,
and then wonder why nothing happens.

Click **Create pull request**.

A bot will say hello back and merge it within a minute or two. Then look at
[hello/](hello/) and you will find yourself in there, alongside everybody else.

---

## Things that will worry you, but are fine

**"detached HEAD"** - you checked out a commit instead of a branch. Nothing is
broken. `git checkout main`.

**An editor opened and you cannot escape** - it is Vim. Press `Esc`, then type
`:q!` and Enter. Use `git commit -m "your message"` to avoid it entirely.

**You deleted or mangled everything** - `git checkout main` then
`git checkout -- .` puts it all back.

**Total confusion** - delete the folder, clone it again. You lose nothing.

---

## Commands worth keeping

```
git clone <url>          download a repository
git status               what is going on right now
git log                  the history          (press q to exit)
git log --oneline        the history, readable
git branch -a            every branch
git checkout <branch>    travel to a branch
git tag -n99             labels, with messages
git blame <file>         who last touched each line
git diff <a> <b>         what changed between two points
git show <hash>:<file>   read a file as it was
git checkout -b <name>   make a new branch
git add <path>           choose what goes in the snapshot
git commit -m "msg"      take the snapshot
git push origin <branch> send it to your fork
```
