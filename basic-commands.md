# ⌨️ Basic commands — copy, paste, done

> 🎯 **Setup → clone → work → push. Everything a beginner needs, as copy-paste blocks.**
> Lines starting with `#` are comments — safe to paste, they're ignored by the terminal.
> Want the *why* behind each command? → [13 · Everyday Git commands](docs/13-everyday-git-commands.md)

---

## 1 · One-time setup (once per computer)

### 1a · Install Git

Download: **[git-scm.com/downloads](https://git-scm.com/downloads)** — then check it works:

```bash
git --version
```

### 1b · Tell Git who you are

Every change you make is stamped with this name and email. Use your **real name** and **FINTEC email**:

```bash
git config --global user.name  "Your Name"
git config --global user.email "you@finther.my"
```

### 1c · Get your access token (the terminal "password")

> ⚠️ GitLab **does not accept your GitLab password** in the terminal — it wants an **access token**.

1. GitLab → click your **avatar** → **Edit profile**
2. Left menu → **Access tokens** → **Add new token**
3. Name: `my-laptop` · set an expiry · tick scopes: `read_repository` + `write_repository`
4. **Create token** → **copy it now** (shown only once!)

Full walkthrough with screenshots-level detail: [10 · Choosing your tool](docs/10-choosing-your-tool.md).

### 1d · Let your computer remember the token

```bash
git config --global credential.helper store
```

*(The next time you type the token, Git saves it and stops asking.)*

---

## 2 · First time: download a project (clone)

Example below uses **this very repo**. For other projects, copy their link from the project page → **`Code` ▾ → Clone with HTTPS**.

```bash
cd ~/Documents                  # go wherever you keep your work
git clone https://gitlab.com/ai-fintec/git-tutorial-fintec.git
cd git-tutorial-fintec          # enter the project folder
```

It will ask:

```text
Username:  your-gitlab-username
Password:  paste-your-ACCESS-TOKEN   ← not your GitLab password!
```

Check it worked:

```bash
git log --oneline               # you should see the history 🎉
```

---

## 3 · Every day: work → commit → push

Do this block top to bottom, replacing the branch name with yours:

```bash
# 1. start from the latest version
git switch main
git pull

# 2. create your own branch (never work directly on main!)
#    tip: <issue-number>-<short-name>  e.g. 12-add-dark-mode
git switch -c my-first-task

# 3. do your work — edit files now, then look at what changed:
git status                      # which files changed?
git diff                        # what exactly changed, line by line?

# 4. save a snapshot (commit)
git add .
git commit -m "Describe what you changed, briefly"

# 5. upload to GitLab (push)
git push -u origin my-first-task
```

After the first push, GitLab prints a **Create merge request** link — click it and follow [19 · Create a Merge Request](docs/19-create-a-merge-request.md). That's how your work gets reviewed and merged.

### More commits on the same branch? Shorter loop:

```bash
# edit files, then:
git add .
git commit -m "Another clear message"
git push                        # no -u needed after the first push
```

---

## 4 · Quick fixes (the common ones)

```bash
git restore filename            # undo UN-saved-in-a-commit edits in one file (really gone!)
git restore --staged filename   # unstage a file (keeps your edits)
git status                      # lost? this always tells you where you are
git log --oneline               # recent history, short list
```

Push was **rejected** (`fetch first`)? Someone pushed before you — normal:

```bash
git pull                        # combine their work with yours
git push                        # try again
```

Merge conflict markers (`<<<<<<<`) appeared? → [22 · Fix merge conflicts](docs/22-fix-merge-conflicts.md) — calm, step by step.
Everything else that can go wrong → [28 · Common mistakes and recovery](docs/28-common-mistakes-and-recovery.md).

---

## 5 · The whole thing at a glance

```text
┌─ ONCE ─────────────────────────────────────────────────┐
│ install git → config name/email → access token         │
│ → git clone https://gitlab.com/ai-fintec/<project>.git │
└────────────────────────────────────────────────────────┘
┌─ EVERY DAY ────────────────────────────────────────────┐
│ git switch main && git pull     ← start fresh          │
│ git switch -c my-branch         ← one task = one branch│
│ …edit files…                                           │
│ git add .                      ← stage                 │
│ git commit -m "message"        ← snapshot              │
│ git push -u origin my-branch   ← first push            │
│ (then: git push)               ← every push after      │
│ → click "Create merge request" ← review & merge        │
└────────────────────────────────────────────────────────┘
```

> 🔐 **Before every commit, 5 seconds:** any password, key, or `.env` in `git status`? Stop → [29 · Security basics](docs/29-security-basics.md).

Stuck? → [30 · "What do I do next?"](docs/30-what-do-i-do-next.md) · **finther.ai@finther.my**
