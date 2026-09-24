# 18 · Pull — keep your copy up to date

> ⏱️ **~7 min** · 🎯 **Level: Beginner** · 🧰 **Tool needed: Git terminal**

---

## Why pulling is a habit, not a chore

While you worked on your branch, the project didn't freeze: teammates merged fixes, docs changed, `main` moved on. **`git pull` downloads those changes into your copy** — and pulling *often* is what keeps merges painless ([12 · concepts](12-git-concepts-in-plain-english.md)).

```
   GITLAB (teammates pushed new work)          YOUR COMPUTER (behind)
   ┌────────────────────────────┐   git pull    ┌────────────────────┐
   │  ●──●──●  newest           │ ───────────▶  │  ●──●──●──●──●  ✅  │
   └────────────────────────────┘   download +  └────────────────────┘
                                    combine
```

## When to pull

| Moment | Pull what |
|---|---|
| Start of your working day | `git switch main` → `git pull` |
| **Before starting any new branch** | same — [14 · Branches](14-branches.md) rule |
| Before pushing (if push was rejected) | `git pull` on your branch |
| Before "I'm done, ready for review" | your branch: `git pull` |
| Honestly: whenever you think of it | current branch 🙂 |

## The two places you'll pull

### 1 · On `main` — refresh the starting line

```bash
git switch main
git pull
```

Typical output:

```text
Updating 4c5b6a7..9f8e7d6
Fast-forward
 calculator.js | 5 +++--
 1 file changed, 3 insertions(+), 1 deletion(-)
```

*Fast-forward* = "you had no local changes; I just moved you forward". The healthy, boring case. 🎉

### 2 · On your branch — absorb what changed elsewhere

```bash
git switch 12-show-total-interest
git pull
```

If nobody touched your branch, Git says `Already up to date.` Done.

## "Pull" = fetch + merge (30-second anatomy)

`git pull` is a shortcut for two steps:

```bash
git fetch    # 1. download new commits, look but don't touch
git merge    # 2. combine them into your current branch
```

90% of the time the shortcut is exactly right. If a **merge conflict** pops up — both branches edited the same lines — Git pauses and asks you to decide: that's a normal, recoverable moment with its own guide:

👉 **[22 · Fix merge conflicts](22-fix-merge-conflicts.md)** *(bookmark it; everyone meets their first conflict eventually)*

## Make it a fresh start: update a long-lived branch

Been on `12-show-total-interest` for three days while `main` moved? Bring `main`'s new work *into* your branch:

```bash
git switch main
git pull
git switch 12-show-total-interest
git merge main        # combine latest main into your branch
```

Same mechanics, explicit direction. Do this every day or two and the final Merge Request review stays small and friendly ([20 · Reviewing](20-review-a-merge-request.md)).

## 🚫 Common problems

| Problem | Fix |
|---|---|
| `error: Your local changes … would be overwritten` | You have unsaved/un-committed edits Git refuses to clobber → commit them first ([16](16-commits.md)), or stash: [Advanced · 04](advanced/04-git-power-moves.md) |
| `CONFLICT (content): Merge conflict in …` | Expected, fixable → **[22 · Fix merge conflicts](22-fix-merge-conflicts.md)** |
| Pulled on the wrong branch | Read the output, `git status`, and see [28 · Common mistakes](28-common-mistakes-and-recovery.md) — almost always fixable calmly |
| "I pulled and now I'm lost" | `git status` + `git log --oneline` tell you exactly where you are; [28](28-common-mistakes-and-recovery.md) · nobody's ruined anything — history just gained commits |

## Pull vs the web alternatives

| You… | Do |
|---|---|
| Just want to *see* the latest files | Browse on gitlab.com — no pull needed 🙂 |
| Want latest files on disk, don't care about Git niceties | `git pull` on `main` |
| Made web/IDE edits (they're commits on GitLab!) | Your local copy is now behind → `git pull` gets them |

That last row is the classic mixed workflow: **edits made on the website still need a pull on your computer.** Remember it and "why does my laptop have old code?" never happens.

## ✅ Check yourself

1. Why pull before creating a branch? → *So your branch starts from the latest `main`, not yesterday's.*
2. What does "Fast-forward" mean? → *You had nothing local to merge — your copy simply advanced.*
3. Pull hit a conflict — now what? → *Calmly follow [22 · Fix merge conflicts](22-fix-merge-conflicts.md).*

---

[⬅️ 17 · Push](17-push.md) · [19 · Create a Merge Request ➡️](19-create-a-merge-request.md)
