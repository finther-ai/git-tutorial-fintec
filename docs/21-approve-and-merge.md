# 21 · Approve and merge

> ⏱️ **~8 min** · 🎯 **Level: Beginner** · 🧰 **Tool needed: web browser**

---

## The finish line

```
Issue → Branch → Work → Commit → Push → Merge Request → Review ✅ → **Merge**
```

Review threads are resolved, approvals are in — the MR can now become part of `main`. This guide is the last mile, and it's mostly buttons.

## Who can press Merge?

- The **author normally doesn't** — someone else signs off. That's the whole point of review ([20 · Reviewing](20-review-a-merge-request.md))
- **Maintainers** can always merge; **Developers** can when the project's settings allow (many teams require Maintainer sign-off or a number of approvals — configured per project, see [Advanced · 03](advanced/03-protected-branches-and-approvals.md))
- Not sure if it's you? The merge widget at the bottom of the MR tells you: **Merge** button = yes · greyed-out with a reason = no (and it names the reason)

## Pre-merge checklist (30 seconds)

Scroll the MR from top:

- [ ] **No unresolved threads** (GitLab shows the count; defaults may even block on it)
- [ ] **Required approvals present** (green ✔ in the widget)
- [ ] **No conflicts** — otherwise: [22 · Fix merge conflicts](22-fix-merge-conflicts.md) first
- [ ] **Description still true** — last read of *What/Why/How to test*
- [ ] **Draft: prefix removed** (if it was a draft — [19](19-create-a-merge-request.md))

## Press Merge

In the merge widget (bottom of the MR) click **Merge**.

GitLab asks about merge options — beginner-safe answers:

| Option | Recommendation |
|---|---|
| **Delete source branch** | ✅ tick (usually default). The branch served its purpose; the history keeps everything ([14 · Branches](14-branches.md)) |
| **Squash commits** | Leave as the project default. Squashing folds your small commits into one — tidier `main`, but you lose the step-by-step story. Team preference; ask your lead ([Advanced · 03](advanced/03-protected-branches-and-approvals.md)) |

> 💡 Sometimes a green **"Merge when pipeline succeeds"** (auto-merge) button appears instead — click it and GitLab merges automatically once checks pass. That's fine.

## What merging does

```
before:  main ──●──●──●            after:  main ──●──●──●──●──● (your work, in)
              \                        branch deleted, issue closed
   12-show-total-interest ●──●
```

1. Your commits land on `main` — visible to the whole team
2. Source branch deleted (if ticked)
3. **`Closes #12` fires** → Issue #12 closes automatically, linked to the MR forever ([24 · Linking](24-link-issues-branches-merge-requests.md))
4. Everyone's next `git pull` ([18](18-pull.md)) receives your work

**The MR page stays up** — permanent record of what changed, why, and who agreed. Gold six months later.

## After merging (author's last mile)

```bash
git switch main
git pull                      # get your own merged work back
git branch -d 12-show-total-interest   # tidy your local copy too
```

Then: pick the next Issue and start the loop again at [14 · Branches](14-branches.md). This *is* the job now. 🎉

## "Merge" vs "Close"

| Button | Effect | Use when |
|---|---|---|
| **Merge** | changes land on the target branch | work is approved (the normal ending) |
| **Close** | MR is archived, **nothing lands** | duplicate MR, abandoned approach, created by mistake. Closing is *fine and cheap* — it's feedback, not failure |

## 🚫 Common problems

| Problem | Meaning / fix |
|---|---|
| **Merge** button greyed: *"X approval required"* | Not enough approvals yet → wait (or ask in the MR politely — never nag 🙂) |
| Greyed: *"Pipeline must succeed"* | Project runs automated checks; they're red → check the **Pipelines** tab, fix, push |
| Greyed: **"This merge request contains merge conflicts"** | → **[22 · Fix merge conflicts](22-fix-merge-conflicts.md)** — routine, not drama |
| Merged, but Issue #12 still open | The description must say `Closes #12` **exactly** — add it, or close the issue manually ([23 · Issues](23-issues.md)) |
| Merged into the wrong branch | Tell your Maintainer immediately — fixable, but sooner beats later ([28 · Common mistakes](28-common-mistakes-and-recovery.md)) |

## ✅ Check yourself

1. Author merges their own MR? → *Normally no — a reviewer/sign-off merges (often a Maintainer).*
2. Two merge options and their beginner defaults? → *Delete source branch ✅ ticked; squash = project default.*
3. Issue didn't auto-close — why? → *Description lacked the `Closes #12` keyword ([24](24-link-issues-branches-merge-requests.md)).*

---

[⬅️ 20 · Review a Merge Request](20-review-a-merge-request.md) · [22 · Fix merge conflicts ➡️](22-fix-merge-conflicts.md)
