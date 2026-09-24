# 12 · Git concepts in plain English

> ⏱️ **~10 min** · 🎯 **Level: Beginner** · 🧰 **Tool needed: none (concepts!)**

---

## Why this guide exists

You're about to learn commands ([13 · Everyday Git commands](13-everyday-git-commands.md)). Commands without concepts are magic spells — they work until they don't, and then you're stuck. **Ten minutes of plain English first makes every later guide click.**

## The six ideas that run everything

### 1 · The repository = file storage + history

Defined back in [01](01-what-is-gitlab.md): one project, all its files, **plus every version of every file since day one**. The history lives in the hidden `.git/` folder inside your clone ([11](11-clone-a-project.md)).

### 2 · Commits = named snapshots

A **commit** is a snapshot of your project at one moment, carrying:

- *what changed* (which files, which lines)
- *who* made it (the name/email you set in [10](10-choosing-your-tool.md))
- *when*, and *why* — the commit message
- a unique code, its "fingerprint": e.g. `a1b2c3d`

History is a chain of these snapshots:

```
a1b2c3d  Add GST field to calculator
9f8e7d6  Fix spelling of "repayment"
4c5b6a7  First version of calculator
```

> 💡 Commits are **cheap and safe**. Committing doesn't publish anything — it saves locally, like Ctrl+S with a memory. Making many small commits is the pro move, not a rookie one.

### 3 · Branches = parallel versions

A **branch** is simply *a movable label pointing at one commit* — a line of work that doesn't disturb others.

```
main:     ──●────●────●────────────►  (the safe, shared version)
                   \
12-show-total-interest:           ●────●──►  (your work, in progress)
```

- `main` — the **default branch**: the shared, "we consider this working" version
- your branch — a private playground copied from `main`; edit freely, nobody else sees it until you ask

Full guide next-but-one: [14 · Branches](14-branches.md).

### 4 · Staging = choosing what goes into the snapshot

Between "I edited files" and "I commit", there's the **staging area**: the list of changes your next commit will include.

```
edit files  ──▶  (working area)
git add …   ──▶  (staging area)   ← you pick the pieces here
git commit  ──▶  snapshot! 📸
```

Why bother? So you can commit *exactly* the related changes and leave experiments out. In practice: `git add file1 file2` (chosen files) or `git add .` (everything — fine while you're new).

### 5 · Push & pull = syncing with GitLab

```
        git push  ──────────────▶   upload your commits to GitLab
        ◀──────────────  git pull    download others' commits from GitLab
YOUR COMPUTER                        GITLAB (the shared master copy)
```

- **push** — your commits travel from your machine to GitLab; *until you push, nobody sees your work*
- **pull** — others' commits (and your own from other machines) come down to you; *do it often, conflicts hate surprises* ([22](22-fix-merge-conflicts.md))

> 📌 Commit ≠ push. Commit = save to your local history. Push = share it. This is the #1 vocabulary mix-up — knowing it puts you ahead.

### 6 · Merge Requests = the polite front door

A **Merge Request (MR)** says: *"Branch `12-show-total-interest` is ready — please review it and merge it into `main`."* It's where teammates comment, request changes, and finally approve. GitLab compares the two branches and shows every changed line.

The FINTEC standard loop, in one line:

```
Issue → Branch → Work → Commit → Push → Merge Request → Review → Merge
```

You'll live this loop in [26 · The FINTEC workflow](26-the-fintec-workflow.md).

## Words you'll overhear (mini-glossary)

| Word | Meaning |
|---|---|
| **repo** | repository, short |
| **clone** | your full local copy + the link to GitLab |
| **`origin`** | the default nickname for "the GitLab copy" of this project |
| **`HEAD`** | "where you are right now" pointer (usually: your current branch) |
| **checkout / switch** | move to another branch |
| **merge** | combine one branch's changes into another |
| **conflict** | two branches changed the same lines; Git asks a human to decide ([22](22-fix-merge-conflicts.md)) |
| **WIP** | work in progress |
| **LGTM** | review comment: "Looks Good To Me" ✅ |
| **PR** | pull request — GitHub's word for a Merge Request; same thing |

## ✅ Check yourself

1. Difference between commit and push? → *Commit saves locally; push uploads to GitLab.*
2. What is `main`? → *The default, shared branch — the "working" version of the project.*
3. What does an MR do? → *Proposes merging your branch into another, with review in between.*

---

[⬅️ 11 · Clone a project](11-clone-a-project.md) · [13 · Everyday Git commands ➡️](13-everyday-git-commands.md)
