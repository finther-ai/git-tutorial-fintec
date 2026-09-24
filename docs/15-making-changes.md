# 15 · Making changes

> ⏱️ **~7 min** · 🎯 **Level: Beginner** · 🧰 **Tool needed: your editor of choice**

---

## Where you are in the loop

```
Issue → Branch ✅ → **Work** → Commit → Push → Merge Request → Review → Merge
```

You have a branch ([14](14-branches.md)). Now you actually *do the task*: edit code, write docs, fix the bug. This guide is about doing that **the Git-safe way**.

## The golden rule of changing things

> **One branch = one task = one logical change.**
> Resist fixing unrelated things "since I'm here anyway". Unrelated changes go on their own branch — small, focused changes review fast; big mixed ones rot in review for weeks ([20 · Reviewing](20-review-a-merge-request.md)).

## The rhythm (it's simpler than you think)

```bash
# 1. make sure you're on YOUR branch
git status                    # → "On branch 12-show-total-interest" ✅

# 2. edit files with whatever you like — VS Code, Vim, anything
#    (edit, save, test, repeat)

# 3. peek at what you changed, as often as you like
git status                    # which files changed?
git diff                      # what exactly changed, line by line?
```

That's it — edit → save → test → repeat. **Nothing is permanent until you commit** ([16 · Commits](16-commits.md)), and nothing leaves your computer until you push ([17 · Push](17-push.md)). You literally cannot disturb anyone while experimenting on your branch.

## Which editor?

| Tool | When it's right |
|---|---|
| **VS Code / your IDE** | Real development work. Its Git panel visualizes status/diff/commit — you'll recognise every concept from this tutorial behind the buttons |
| **GitLab Web IDE** | Quick multi-file changes from any machine — [09 · Create and upload files](09-create-and-upload-files.md) |
| **GitLab web editor** | One-file fixes (pencil icon ✏️) — [09](09-create-and-upload-files.md) |

## Working example (running all the way through the tutorial)

**Issue #12 · "Show total interest paid over the loan lifetime"** on project `ai-fintec/loan-calculator`, your branch `12-show-total-interest`:

1. `git status` → confirm you're on your branch
2. Open `calculator.js` (say), add the total-interest calculation
3. Update the page so the new number displays under the payment table
4. Run/test it locally — make sure it works *before* committing
5. `git status` → shows the two changed files. Exactly what you intended? ✅
6. `git diff` → skim every changed line. Surprise lines? Investigate now, not in review

You're ready to commit: **[16 · Commits](16-commits.md)** → then push: **[17 · Push](17-push.md)**.

## Small habits that separate professionals

- **Run the project before you commit** — "works on my machine" starts with checking *your* machine 🙂
- **`git diff` before every commit** — you'll catch stray debug lines and accidental edits
- **Update related docs in the same branch** — if your change makes the README wrong, fix the README in the same Merge Request
- **New file? Double-check it's not a secret** — `config.env`, API keys, anything credential-shaped: stop, read [29 · Security basics](29-security-basics.md) *before* committing

## 🚫 "Oops" prevention

| Oops | Prevention |
|---|---|
| Edited files on the wrong branch | `git status` **before** editing — always |
| Broke everything with an experiment | It's fine — `git restore <file>` discards un-committed edits ([13](13-everyday-git-commands.md)); committed? [28](28-common-mistakes-and-recovery.md) has you |
| `main` is "dirty" with half-finished edits | Don't edit on `main` 🙂 — switch to a branch first ([14](14-branches.md)) |

## ✅ Check yourself

1. What's the golden rule of a branch? → *One branch, one task, one logical change.*
2. Does editing a file on your branch disturb anyone? → *No — nothing is shared until you push.*
3. Which two commands show *what* changed before you commit? → *`git status` (which files) and `git diff` (which lines).*

---

[⬅️ 14 · Branches](14-branches.md) · [16 · Commits ➡️](16-commits.md)
