# 19 · Create a Merge Request

> ⏱️ **~10 min** · 🎯 **Level: Beginner** · 🧰 **Tool needed: web browser (or terminal, shown too)**

---

## Where you are in the loop

```
Issue → Branch → Work → Commit → Push ✅ → **Merge Request** → Review → Merge
```

Your branch is pushed to GitLab. Now you formally ask: *"Please review my branch and merge it into `main`."* That request is a **Merge Request (MR)** — the heart of how FINTEC ships work ([12 · concepts](12-git-concepts-in-plain-english.md)).

## What an MR actually is

GitLab compares your branch with `main` and shows:

- 📋 **Every changed file and line**, old vs new, side by side
- 💬 **A discussion thread** — comments, questions, approvals
- ⚖️ **A decision gate** — Merge ✅ / request changes ❌, with a full record kept forever

Nothing reaches `main` around an MR. That's the point — see [14 · Branches](14-branches.md).

## Create it — Way 1 · the link after push (easiest)

After your first `git push -u origin <branch>` ([17](17-push.md)), GitLab prints a **"Create merge request"** link. Click it → the MR form opens, pre-filled. Skip to *Filling in the form* below.

## Create it — Way 2 · from the GitLab website

1. Open the project → GitLab usually shows a **yellow banner** at the top: *"You pushed to branch `12-show-total-interest` … [Create merge request]"* → click it, done.
2. Banner gone? Left sidebar → **Code → Merge requests → New merge request**
3. **Source branch:** `12-show-total-interest` · **Target branch:** `main` → **Compare branches and continue**

## Create it — Way 3 · from the Issue (the FINTEC favourite ✨)

If you created the branch from the Issue via **Create merge request** ([14 · Way 3](14-branches.md)), the MR **already exists** — in draft, linked to the issue. You're ahead of schedule; just polish the form.

## Filling in the form

| Field | What to write | Example |
|---|---|---|
| **Title** | One clear sentence, imperative | `Show total interest paid under the payment table` |
| **Description** | **What** changed, **why**, and **how to test it** | see below |
| **Reviewer(s)** | Pick who should review ([20 · Reviewing](20-review-a-merge-request.md)) | `Ahmad` |
| **Delete source branch when merged** | ✅ keep ticked (default) — good hygiene | ✅ |
| **Squash commits** | Leave default unless your team says otherwise ([Advanced · 03](advanced/03-protected-branches-and-approvals.md)) | — |

### A description that reviewers love

```markdown
## What
Adds a total-interest figure under the payment table.

## Why
Closes #12 — customers asked to see the full cost of the loan, not just monthly instalments.

## How to test
1. Open the calculator, enter amount 20000, 5 years, 4.5%
2. Total interest row shows RM2,581.49 ✅
3. Empty amount field → no NaN, shows "—"
```

> 🔗 See that `Closes #12`? **Type it — it's load-bearing.** When this MR merges, GitLab **automatically closes Issue #12**, and the MR shows up inside the issue forever. Full mechanics: [24 · Linking Issues, Branches and Merge Requests](24-link-issues-branches-merge-requests.md).

### Not finished yet? Make it a Draft

Prefix the title with **`Draft:`** (e.g. `Draft: Show total interest…`). Draft MRs:

- can't be merged until you remove the prefix ✅
- still let teammates **see your progress early** — opening a Draft on day one of a long task is a pro move, not a confession 🙂

Then click **Create merge request**. 🎉 Your MR now has its own page with a number: `!13`, say.

## What happens next

1. Your reviewer gets a notification and reads your diff: [20 · Review a Merge Request](20-review-a-merge-request.md)
2. Comments arrive → you respond and push more commits to the **same branch** — the MR updates automatically, no new MR needed
3. Approved → **[21 · Approve and merge](21-approve-and-merge.md)**
4. Branch deleted, `main` updated, Issue #12 auto-closed → coffee ☕

## While you wait for review

Don't idle. Start the next issue on a **new branch** — multiple branches per person is normal and fine.

## 🚫 Common problems

| Problem | Fix |
|---|---|
| "The changes are huge / nothing like what I did" | Your branch started from an old `main` → update it: `git switch <branch>` → `git merge main` ([18 · Pull](18-pull.md)) |
| MR says **"Merge blocked: pipeline must succeed"** or similar | Ask your lead about the project's merge checks — some are configured per project ([Advanced · 03](advanced/03-protected-branches-and-approvals.md)) |
| MR says **conflicts** | Normal, fixable: **[22 · Fix merge conflicts](22-fix-merge-conflicts.md)** |
| Pushed more commits but the MR didn't update | It does, give it a second — MR tracks the *branch*, not the push |
| Created MR from the wrong source branch | Close it (no harm — MRs are free), fix, create again |

## ✅ Check yourself

1. MR source and target, in our example? → *source `12-show-total-interest`, target `main`.*
2. Which two description lines reviewers need most? → *Why (issue link) + How to test.*
3. Work not finished — blocked from opening an MR? → *No: title it `Draft:` and open it anyway.*

---

[⬅️ 18 · Pull](18-pull.md) · [20 · Review a Merge Request ➡️](20-review-a-merge-request.md)
