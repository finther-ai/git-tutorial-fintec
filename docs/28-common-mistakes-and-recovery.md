# 28 · Common mistakes — and how to recover

> ⏱️ **~12 min** · 🎯 **Level: Beginner (keep as reference!)** · 🧰 **Tool needed: terminal, mostly**

---

## Read this when calm, use it when panicking

**You cannot lose committed work by accident.** Git's whole design is *never overwrite, always append* — nearly every "disaster" is one command from fixed. This is your first-aid manual: find the symptom, follow the fix.

> 🚑 The three questions that diagnose *any* Git panic:
> 1. `git status` — where am I, what's changed?
> 2. `git log --oneline` — what does my history look like?
> 3. *Have I pushed it?* — pushed = shared, un-pushed = private (much easier to fix — [12 · concepts](12-git-concepts-in-plain-english.md))

## 🩹 The fixes

### 1 · "I edited a file and wrecked it — I want my last saved version back"

```bash
git restore calculator.js
```

Discards **un-committed** edits in that file → back to the last commit. 🔥 *For real: the edits are gone* — that's the point. Uns nurture. Committed it already? → #3.

### 2 · "I committed — but I meant to change one more thing"

```bash
# add the fix, then fold it into the last commit:
git add .
git commit --amend          # keeps the message, absorbs the new changes
git commit --amend -m "Better message"   # or fix the message too
```

> ⚠️ Amend **only un-pushed commits**. Amending something already pushed rewrites shared history — see #9.

### 3 · "My last commit message is embarrassing / wrong"

```bash
git commit --amend -m "Fix NaN when loan amount is empty"
```

Same rule as #2: un-pushed only.

### 4 · "I committed to the wrong branch" *(classic!)*

You made commits on `main` before realising:

```bash
# 1. create a branch pointing at your work (nothing is lost — it's a bookmark)
git branch 12-show-total-interest

# 2. move main back to GitLab's version…
git switch main
git reset --keep origin/main

# 3. …and continue on your branch
git switch 12-show-total-interest
```

`reset --keep` moves the branch label and keeps your files sane. If `main` is protected and rejects the later push — it should! — the story ends even more safely: you *couldn't* have shared it.

### 5 · "I staged a file I didn't mean to stage"

```bash
git restore --staged secrets-draft.md    # unstages — your edits stay on disk
```

(`git add .` enthusiasm, cured one file at a time — [13](13-everyday-git-commands.md).)

### 6 · "I'm mid-task and Git refuses to switch/pull"

```text
error: Your local changes … would be overwritten
```

Git is *protecting* un-committed work. Commit it first — the honest move:

```bash
git add . && git commit -m "WIP: halfway through interest panel"
```

or shelve it briefly: `git stash` → later `git stash pop` ([Advanced · 04 · Git power moves](advanced/04-git-power-moves.md)).

### 7 · "Push rejected — `! [rejected] … fetch first`"

Teammate pushed first. Not an error — an order of operations ([17 · Push](17-push.md)):

```bash
git pull          # combine; resolve a conflict if one appears — [22]
git push
```

**Never** reach for `git push --force` here. Ever.

### 8 · "Conflict markers are in my file and I'm lost"

```text
<<<<<<< HEAD
=======
>>>>>>> main
```

Deep breath: edit the block into its correct final form, delete all three marker lines, `git add`, `git commit`. Full walkthrough: **[22 · Fix merge conflicts](22-fix-merge-conflicts.md)**. Truly lost? `git merge --abort` → back to exactly where you were. Zero damage.

### 9 · "I amended / rewrote a commit that was already pushed"

Push now fails (`rejected · non-fast-forward`). If *nobody else* branched from it:

```bash
git pull --rebase     # replays your work on top; resolve conflicts if asked
git push
```

If others *did* pull your work: stop rewriting, make a **new normal commit** instead, and mention it in the MR. And internalise the rule: **pushed history is public — you add to it, you don't rewrite it.** (Force-push is blocked on protected branches anyway — by design.)

### 10 · "I merged something that shouldn't have merged"

Don't rebuild history — **reverse it forward**. On the merged MR page, **Revert** creates a *new* MR that undoes the change (review it like any MR — [20](20-review-a-merge-request.md)). Prefer that over hand-rolled fixes; the revert commit documents itself.

### 11 · "My local copy is a mess and I want to start over"

Nuclear option — **it deletes un-pushed local work**, so read twice:

```bash
git fetch origin
git reset --hard origin/main        # local main = GitLab's main, exactly
```

Un-pushed commits and un-committed edits **on that branch** are gone. If that thought scares you: commit or push first — then nothing is ever lost.

### 12 · "I deleted a branch I still needed"

```bash
git switch main
git pull
git branch 12-show-total-interest origin/12-show-total-interest   # restore from GitLab's copy
```

Even fully-deleted-locally, GitLab remembers recently deleted branches (project → **Code → Branches**) — and a **merged** branch's commits live in `main`'s history forever regardless. Branches are labels; labels are cheap.

### 13 · "I committed a password / API key / .env file" 🚨

**Treat it as leaked from minute zero.** Deleting the file in a new commit does **not** remove it from history.

1. **Revoke/rotate the credential immediately** — that's the real fix
2. Tell your Maintainer/lead — don't hide it, everyone does this once
3. Then clean-up guidance: **[29 · Security basics](29-security-basics.md)**

### 14 · "GitLab is down / I can't reach it"

Rare, but: your local clone keeps working — code, commits, branches all local ([12 · concepts](12-git-concepts-in-plain-english.md)). Keep committing locally; push when GitLab returns. This is the design working.

## The meta-lesson

| When afraid… | Actually do |
|---|---|
| "I'll hide this mistake" | surface it — a Maintainer un-sticks you in minutes |
| "I'll force-push to fix history" | add a new commit instead — history is a log, not a whiteboard |
| "I'll do it in prod to test" | sandbox project ([08](08-create-a-project-from-scratch.md)) — Git mistakes are *free* there |

The people who seem calmest about Git aren't people who never make mistakes — they're people who know every mistake above is recoverable. Now you do too. For anything off this list: [30 · What do I do next?](30-what-do-i-do-next.md), or **finther.ai@finther.my**.

## ✅ Check yourself

1. Push was rejected. Force? → *Never. `git pull` → resolve → push.*
2. Committed a secret — first move? → *Rotate/revoke the credential, then tell your lead.*
3. Want to undo a pushed, merged change? → *The MR's **Revert** button — a new, normal MR.*

---

[⬅️ 27 · Project walkthrough](27-project-walkthrough.md) · [29 · Security basics ➡️](29-security-basics.md)
