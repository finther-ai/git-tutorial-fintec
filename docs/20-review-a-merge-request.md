# 20 · Review someone else's Merge Request

> ⏱️ **~10 min** · 🎯 **Level: Beginner** · 🧰 **Tool needed: web browser**

---

## Why review exists

**Review is not an exam — it's how FINTEC keeps `main` trustworthy and spreads knowledge around the team.** Every MR gets at least one other pair of eyes before merge ([19 · Create a Merge Request](19-create-a-merge-request.md)). As a reviewer you're not guarding a gate; you're lending your brain.

## Finding MRs that need you

Two usual routes:

1. **You got assigned** — GitLab emails you / shows the MR under avatar → **Merge requests → Assigned to you**
2. **Team courtesy** — left sidebar → **Code → Merge requests** → *Open* tab. Long-waiting MRs are exactly where quality quietly dies: peek at the list when you have 15 minutes.

## How to actually read an MR

Open the MR page. Recommended order:

| Step | Where | What you're doing |
|---|---|---|
| 1️⃣ Read the **description** | Top | *What* did they claim to change, and *why*? Does it link the issue (`Closes #12`)? |
| 2️⃣ Read the **commits** tab | Tab bar | The story in small steps — usually tells you the author's intent |
| 3️⃣ Read the **Changes** tab | Tab bar | The actual diff: red lines = removed, green lines = added |
| 4️⃣ Check **how to test** | Description | Can you verify their claim? If instructions are missing — that itself is worth a comment 🙂 |

**Reading the diff well:**

- Read the *changed lines first*, then their *surroundings* — context is where surprises hide
- Big diffs? Collapse boring files in the file tree; review the core change first
- Something looks wrong and you're not sure? **Say exactly that** — "this looks inverted, but I might be misreading" is a *great* review comment

## Commenting: kind, specific, useful

Comment on any line: hover it → click the **💬 comment icon** → type → **Start a review** (batches your comments; **Finish review** delivers them all at once — much nicer than 14 notification pings).

| ❌ Not useful | ✅ Useful |
|---|---|
| `this is wrong` | `This divides by zero when the term is 0 years — reproduce with amount=20000, term=0` |
| `why??` | `Question: why a global here instead of passing it into `monthlyPayment()`?` |
| `rename this variable` | `Nit: `mi` → `monthlyInterest`? Saves a mental decode on the next reader` |

### The tone that makes teams work

- 🎯 **Critique the code, never the coder.** "This function has a bug" — fine. "You always forget edge cases" — never.
- 🤔 **Ask before you assert.** Plenty of "bugs" are context you don't have yet.
- 🏷️ **Grade your comments** so authors can triage:

| Prefix | Meaning | Blocks merge? |
|---|---|---|
| `Blocking:` | must fix before merge | ✅ yes |
| `Question:` | I need to understand | until answered |
| `Nit:` | polish, author's call | ❌ no |
| `Praise:` 🎉 | say the good thing out loud | — |

*Praise is a real review skill. When someone solves something elegantly — say so in the MR. It costs one line.*

## The review loop (from the author's side)

You'll be the author next week, so know what you're causing 🙂 — the author:

1. reads your comments and replies (or fixes and **pushes to the same branch** — the MR updates live)
2. marks threads **resolved** when settled
3. re-requests your review

Review round two: you only need to look at **what changed since last time** — GitLab marks resolved threads and new commits.

> 💡 **Review speed is team oxygen.** A 24-hour review turnaround keeps everyone flowing; a week-long one teaches authors to fear MRs. If you can't review promptly, say so and hand it to someone who can.

## When *you're* not the code expert

Review anyway, at your level:

- Does the description make sense? Is it testable? → reviewable by anyone
- Docs, naming, README updates → reviewable by anyone
- Deep algorithm correctness → beyond you? Ask a question (`Question: could you walk me through the edge case?`) and **also tag the team lead**. Honest limits beat silent approvals.

## Approving

Satisfied? The **Approve** button sits below the MR (or in the merge-widget area). What approval means and who can press the final **Merge** button: 👉 **[21 · Approve and merge](21-approve-and-merge.md)**

## 🚫 Common problems

| Problem | Move |
|---|---|
| 800-line MR lands in your lap | Review the description + core files, comment `Blocking: please split — see [15 · golden rule](15-making-changes.md)`; splitting is kinder than a rubber-stamp |
| Author disagrees with your comment | Discuss in the thread — their context may beat your instinct. Deadlock? Loop in the Maintainer, calmly |
| You approved, then noticed a real bug | You can **Unapprove** and comment immediately — honesty in the thread beats silent regret |

## ✅ Check yourself

1. Review's purpose? → *Shared quality + shared knowledge — not gatekeeping.*
2. Which comments block a merge? → *`Blocking:` (and unresolved `Question:`).*
3. Author pushed a fix — what do you re-review? → *The new commits and resolved threads since your last look.*

---

[⬅️ 19 · Create a Merge Request](19-create-a-merge-request.md) · [21 · Approve and merge ➡️](21-approve-and-merge.md)
