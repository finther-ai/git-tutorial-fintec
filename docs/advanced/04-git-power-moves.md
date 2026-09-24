# Advanced · 04 · Git power moves — stash, rewrite, and history archaeology

> ⏱️ **~12 min** · 🎯 **Level: Optional — read after the main path** · 🧰 **Tool needed: terminal**

---

## What counts as a "power move"

Everything in the main path ([13 · Everyday Git commands](../13-everyday-git-commands.md)) is safe-by-design. These commands are **more powerful and less forgiving** — each has a moment where it's exactly right, and a misuse pattern to respect. Learn them *after* the loop is muscle memory ([26 · The FINTEC workflow](../26-the-fintec-workflow.md)).

## 1 · `git stash` — "shelve everything, now"

**The moment:** interrupted mid-task (urgent bug!), but your half-done edits don't commit cleanly and you can't switch branches ([28 · #6](../28-common-mistakes-and-recovery.md)).

```bash
git stash            # edits vanish into a shelf; working dir goes clean
git switch main && git pull && git switch -c 17-fix-urgent-nan
# …do the urgent fix, commit, push, MR…
git switch 12-show-total-interest
git stash pop        # edits return, exactly as left
```

| Command | Effect |
|---|---|
| `git stash` | shelve tracked-file changes (name it: `git stash push -m "interest panel WIP"`) |
| `git stash list` | see the shelf — stashes stack! |
| `git stash pop` | apply the newest stash **and remove it** |
| `git stash apply` | apply but *keep* the copy |
| `git stash drop` | delete a stash — 🔥 gone for good |

> ⚠️ The classic accident: `git stash` today, `pop` next Tuesday onto the *wrong* branch, confusion. Stash is a **drawer, not storage** — empty it within hours, not weeks. Real persistence = a commit ([16](../16-commits.md)), even a `WIP:` one.

## 2 · `git log` archaeology — "who changed this line, and why?"

```bash
git log --oneline --graph --all          # the branch map of everything
git log -p calculator.js                 # every change to one file, with diffs
git log -S "totalInterest" --oneline     # every commit that added/removed that string 🔍
git blame calculator.js                  # last person to touch each line (and when)
```

`blame` gets a bad reputation as a blame-assigning tool. Its real use is generous: *find the commit that touched the line, read its message and MR, and you have the why* — the whole reason FINTEC keeps history at all ([12 · concepts](../12-git-concepts-in-plain-english.md)). On GitLab, open a file → **Blame** button: same thing, clickable, prettier.

## 3 · `git rebase` — linear history, carefully

`git merge main` into your branch ([18 · Pull](../18-pull.md)) creates a merge commit: honest but branchy. **Rebase is the alternative:** replay your commits *on top of* the latest `main`, as if you'd started from it.

```bash
git switch 12-show-total-interest
git fetch origin
git rebase origin/main
```

| | `merge` | `rebase` |
|---|---|---|
| History | shows the true branch structure | linear, tidy reading |
| Risk | none | **rewrites your commits** → new fingerprints |
| Beginner default | ✅ | optional polish |

**The iron rule:** rebase **your own, un-pushed (or knowingly yours-alone) branch** — never a branch others build on, never `main`. Rebase rewrites commit identity; anyone holding the old commits gets a mess ([28 · #9](../28-common-mistakes-and-recovery.md) is the same story from the other side).

Rebase conflict? Same mechanics as merge conflicts ([22 · Fix merge conflicts](../22-fix-merge-conflicts.md)), but per replayed commit: fix → `git add` → `git rebase --continue`. Escape hatch: `git rebase --abort` — exactly back to the start. The abort button always works. 🙂

## 4 · Reflog — the safety net under the safety net

**The one command that rescues "I did a power move and now everything's gone":**

```bash
git reflog
# a1b2c3d HEAD@{0}: rebase (finish)
# 9f8e7d6 HEAD@{1}: rebase (start)
# 4c5b6a7 HEAD@{2}: commit: Show total interest paid   ← where you were before
git reset --hard HEAD@{2}      # or: git branch rescue-branch 4c5b6a7
```

Reflog records *where HEAD has ever been* in your local repo, for months — including before a bad reset/rebase/amend. Git almost never actually deletes committed work; it just moves labels. Reflog finds where the label used to be. **The command to know before you need it** — like the fire exit.

## 5 · Interactive staging — commit in deliberate pieces

Half a file belongs in commit A, half in commit B?

```bash
git add -p          # offers each change-chunk: y (stage) / n (skip) / s (split) / ? (help)
git commit -m "Fix NaN guard"          # piece one
git add -p && git commit -m "Add tooltip"   # piece two
```

Matches the "one commit = one logical change" ideal from [16 · Commits](../16-commits.md). Worth knowing; the Web IDE's staging panel does the same job visually if prompts feel dense.

## 6 · Bisect — find the commit that broke it (the demo-friendly one)

Somewhere in the last 200 commits, a bug appeared. `git bisect` binary-searches them for you:

```bash
git bisect start
git bisect bad                  # current HEAD is broken
git bisect good 4c5b6a7         # this old commit was fine
# Git checks out a middle commit; you test, then answer:
git bisect good                 # or: git bisect bad
# …~7 rounds for 200 commits; Git names the culprit commit
git bisect reset                # back to reality
```

You rarely need it — but when a regression has no obvious suspect, it turns an afternoon into fifteen minutes. Great party trick in front of management. 🎩

## The power-move etiquette

| Rule | Why |
|---|---|
| Power moves on **your branches only** | shared history is append-only ([28 · #9](../28-common-mistakes-and-recovery.md)) |
| Every scary command has an **abort/reset** — learn it *first* | `--abort`, `reflog`, `ORIG_HEAD` are your seatbelts |
| If it needs `--force`, stop and think | the answer is almost always "no" — especially on shared branches |
| Before a rewrite: `git branch backup-before-rewrite` | a one-second bookmark that makes any experiment free |

> 📌 **The real power move is not needing these.** Small branches, frequent commits, quick merges, honest messages — the beginner loop *is* the advanced skill, executed consistently. Everything here is repair tooling for when reality interrupts the loop.

---

[⬅️ Advanced · 03 · Protected branches & approvals](03-protected-branches-and-approvals.md) · [🏠 Back to the guide map](../../README.md)
