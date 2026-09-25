# 13 · Everyday Git commands (the only ones you need at first)

> ⏱️ **~10 min** · 🎯 **Level: Beginner** · 🧰 **Tool needed: Git terminal** ([10 · setup](10-choosing-your-tool.md))

---

## The honest truth

Day-to-day Git uses about **six commands**. The rest you look up when needed. Learn these six and you can do your job.

## The six

### 1 · `git status` — "what's going on?" 🔍

```bash
git status
```

Tells you: which branch you're on, which files you changed, what's staged. **Run it constantly** — before and after everything. It's read-only: it can *never* break anything.

### 2 · `git switch -c <name>` — start a new line of work 🌿

```bash
git switch -c 12-show-total-interest
```

Creates a new branch and moves you onto it. (Details: [14 · Branches](14-branches.md).)

### 3 · `git add <files>` — pick what to snapshot 📥

```bash
git add calculator.py          # one file
git add .                      # everything changed
```

Moves your changes into the **staging area** — the "will be in the next commit" list ([12 · concepts](12-git-concepts-in-plain-english.md)).

### 4 · `git commit -m "message"` — take the snapshot 📸

```bash
git commit -m "Show total interest paid under the payment table"
```

Saves a named snapshot **to your computer only**. Messed up the message? `git commit --amend -m "better message"` fixes the *latest* one (before pushing — see [28 · Common mistakes](28-common-mistakes-and-recovery.md)).

### 5 · `git push` — upload your snapshots ☁️

```bash
git push -u origin 12-show-total-interest   # first push of a branch
git push                                    # every push after
```

Uploads your commits to GitLab. The `-u origin <branch>` on the first push says "this local branch belongs to that GitLab branch" — after that, plain `git push` remembers. (Details: [17 · Push](17-push.md).)

### 6 · `git pull` — download others' snapshots ⬇️

```bash
git pull
```

Fetches new commits from GitLab and merges them into your current branch. **Start your day and start every task with it.** (Details: [18 · Pull](18-pull.md).)

## The day-loop, assembled

```bash
git pull                    # 1. get up to date
git switch -c 15-fix-nav    # 2. new branch
# …you work, edit files…    # 3. do the task
git status                  # 4. check what changed
git add .                   # 5. stage it
git commit -m "Fix mobile navigation overlap"
git push -u origin 15-fix-nav   # 6. share it
# → open a Merge Request [19]
```

Six commands. That's the job. 🎯

> ⌨️ **Prefer pure copy-paste?** → **[basic-commands.md](../basic-commands.md)** — the whole flow (setup → clone → work → push) as paste-ready blocks, using this repo as the example.

## Reference tables

### Look (read-only — safe, run anytime)

| Command | Question it answers |
|---|---|
| `git status` | What did I change? Where am I? |
| `git log --oneline` | Recent commits, as a short list |
| `git log --oneline --graph --all` | The same, with branch picture |
| `git diff` | What exactly changed, line by line (unstaged) |
| `git diff --staged` | Same, for what's staged |
| `git branch` | Which branches exist locally; `*` = current |

### Move (change where you are / what's staged)

| Command | Effect | Danger |
|---|---|---|
| `git switch <branch>` | Move to an existing branch | none (commit first — see [28](28-common-mistakes-and-recovery.md)) |
| `git switch -c <branch>` | New branch + move to it | none |
| `git add <file>` / `git add .` | Stage changes | none |
| `git restore <file>` | **Discard edits** in a file (un-committed!) | 🔥 loses the edits — really gone |
| `git restore --staged <file>` | Unstage (keeps your edits) | none |
| `git push -u origin <branch>` | First push of a branch | none |
| `git pull` | Download + merge new commits | conflicts possible → [22](22-fix-merge-conflicts.md) |

> 🚨 **Undo commands live in their own guide:** [28 · Common mistakes and recovery](28-common-mistakes-and-recovery.md). Don't improvise undo with `--force` flags — ever.

## Cheatsheet card (print me)

```text
┌───────────────────── FINTEC DAILY GIT ─────────────────────┐
│ git status              what changed?                      │
│ git pull                get the latest                     │
│ git switch -c <branch>  start work                         │
│ git add .               stage everything                   │
│ git commit -m "msg"     snapshot                           │
│ git push -u origin <b>  first push   (then: git push)      │
│ ────────────────────────────────────────────────────────── │
│ git log --oneline       history · git diff   what changed  │
│ git switch <branch>     change branch                      │
└────────────────────────────────────────────────────────────┘
```

## ✅ Check yourself

1. Which command can never break anything? → *`git status` (and `log`, `diff` — all read-only).*
2. `git add .` stages everything — good or bad? → *Good while new; later, stage deliberately so commits stay focused.*
3. What does `-u origin <branch>` do? → *Links your local branch to GitLab on the first push, so plain `git push` works after.*

---

[⬅️ 12 · Git concepts in plain English](12-git-concepts-in-plain-english.md) · [14 · Branches ➡️](14-branches.md)
