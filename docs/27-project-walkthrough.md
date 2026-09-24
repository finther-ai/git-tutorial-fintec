# 27 · A real FINTEC project, start to finish

> ⏱️ **~15 min** · 🎯 **Level: Beginner · capstone** · 🧰 **Tool needed: none to read, sandbox to try**

---

## What this is

Every previous guide, assembled into **one continuous story** — a small FINTEC product taken from *nothing* to *first merged feature*, with every decision explained. Read it as a story; then replay it in a sandbox of your own ([08 · Create a project](08-create-a-project-from-scratch.md)).

**The cast:**

| Person | Role | GitLab role ([06](06-roles-and-permissions.md)) |
|---|---|---|
| **Ahmad** | Team lead | Maintainer |
| **Siti** | Developer (new-ish 👋) | Developer |
| **Mei Ling** | Business analyst | Reporter |

**The product:** `loan-calculator` — a small web app estimating monthly loan repayments for FINTEC customers.

## Phase 0 · The project is born

Ahmad creates the home for the work ([08](08-create-a-project-from-scratch.md)):

- **➕ New → Create blank project**
- Name `loan-calculator`, URL `ai-fintec/loan-calculator` — in the **group**, not his personal namespace
- Visibility **Private** · ✅ *Initialize with a README*
- Writes a real README first commit: what it does, how to run, who to ask ([25](25-readme-and-documentation.md))
- **Manage → Members:** adds Siti as **Developer**, Mei Ling as **Reporter**

> 💡 Reporter for Mei Ling is deliberate: she manages Issues and reads code, but doesn't push code. Lowest role that does the job — [06 · Roles](06-roles-and-permissions.md).

## Phase 1 · The request arrives properly

Mei Ling hears from customer support: *"people want to know the total cost of the loan, not just the monthly payment."* Instead of a chat message that dies by Friday, she files it ([23 · Issues](23-issues.md)):

> **Issue #12** — `Show total interest paid over the loan lifetime`
>
> **Goal:** under the monthly payment, show the total interest for the whole term.
> **Why:** support gets this question weekly; it's a trust-builder for the quotes we send.
> **Acceptance:** amount RM20,000 / 5 years / 4.5% → total interest **RM2,581.49**, shown under the payment.

Mei Ling adds label `feature`, assigns nobody — Siti will claim it.

## Phase 2 · Siti starts the loop

Siti's morning, in order ([26 · workflow](26-the-fintec-workflow.md)):

```bash
git clone https://gitlab.com/ai-fintec/loan-calculator.git   # day one only — [11]
cd loan-calculator
git switch main && git pull        # fresh starting line — always — [18]
```

She opens Issue #12 → **Assignee: herself** → clicks **Create merge request** ([24 · linking](24-link-issues-branches-merge-requests.md)). GitLab hands her:

- branch `12-show-total-interest` — from fresh `main` ✅
- a **Draft** MR with `Closes #12` already in the description ✅

> 💡 The Draft sits there from minute one. If Ahmad wonders mid-week what Siti is doing, the answer is one click away — no status meeting required.

## Phase 3 · The work

Siti edits `calculator.js` and `index.html` ([15 · making changes](15-making-changes.md)):

```js
// before
function monthlyPayment(amount, years, rate) { /* … */ }

// after — adds the total-interest computation
function totalInterest(amount, years, rate) {
  const months = years * 12;
  const payment = monthlyPayment(amount, years, rate);
  return payment * months - amount;
}
```

Then the panel under the payment table shows the figure; empty amount → `"—"` (she's read about the NaN bug — `#17` — and refuses to reproduce it).

**Before her first commit, the 5-second scan** ([16 · Commits](16-commits.md)):

```bash
git status        # calculator.js, index.html — exactly the two I touched ✅
git diff          # reads like the feature, no debug lines, no secrets ✅
```

```bash
git add .
git commit -m "Show total interest paid under the payment table"
```

```bash
git push -u origin 12-show-total-interest    # first push — [17]
```

GitLab's push reply offers a *Create merge request* link — already covered by her Draft. She opens the MR page and **fleshes out the description** ([19](19-create-a-merge-request.md)):

```markdown
## What
Adds total-interest computation and displays it under the payment table.

## Why
Closes #12 — support gets "what's the total cost?" weekly (request via @meiling).

## How to test
1. Amount 20000, 5 years, 4.5% → total interest shows RM2,581.49
2. Clear the amount → shows "—", never NaN (see #17)

Removes the Draft: prefix → assigns **Ahmad** as reviewer.
```

## Phase 4 · Review

Ahmad gets the notification and reads the MR ([20 · Reviewing](20-review-a-merge-request.md)): description first, commits tab, then the Changes diff line by line.

He leaves two comments, delivered as one review:

> **Nit:** `ti` → `totalInterestValue`? Saves every future reader a mental decode.
>
> **Praise:** the `"—"` for empty input is exactly the right call. 🎉

Siti fixes the nit, `git add . && git commit -m "Rename ti to totalInterestValue" && git push` — the MR updates itself; Ahmad re-glances, approves ✅.

## Phase 5 · Merge — and the machine closes the loop

Ahmad opens the MR: no unresolved threads, approval in, no conflicts → **Merge** ([21](21-approve-and-merge.md)), **Delete source branch ✅**.

Automatic chain reaction ([24](24-link-issues-branches-merge-requests.md)):

1. commits land on `main`
2. branch `12-show-total-interest` deleted
3. **Issue #12 closes itself** — stamped *"Closed via merge request !13"*

Siti tidies up and moves on:

```bash
git switch main && git pull                      # my merged work, back on main
git branch -d 12-show-total-interest             # local tidy-up
```

Total elapsed: two working days. Trail, forever: Issue #12 → branch → MR !13 → review discussion → merge. **Nobody had to remember anything.**

## Epilogue · the loop repeats

- **#17** (`NaN on empty amount`) gets its own Issue, branch `17-fix-safari-nan-bug`, MR `Closes #17` — same loop, smaller diff
- Mei Ling files requests as Issues; Ahmad sees velocity on the board ([23](23-issues.md))
- A week later, Siti and Raj edit line 20 on *different* branches, Raj merges first, and Siti meets her **first conflict** — handled calmly with [22 · Fix merge conflicts](22-fix-merge-conflicts.md). It happens to everyone; now it's routine.

## Your replay checklist

- [ ] Sandbox project ([08](08-create-a-project-from-scratch.md)) — personal namespace is fine
- [ ] Issue with acceptance criteria ([23](23-issues.md))
- [ ] **Create merge request** from the Issue ([24](24-link-issues-branches-merge-requests.md))
- [ ] Small change → scan → commit → push ([15](15-making-changes.md)–[17](17-push.md))
- [ ] Polish the MR description, remove `Draft:` ([19](19-create-a-merge-request.md))
- [ ] Merge, watch the Issue close itself ([21](21-approve-and-merge.md))
- [ ] `git switch main && git pull` — feel the circle close

When that checklist feels boring — **boring is mastery here** — you're ready for real FINTEC work. 🎉

---

[⬅️ 26 · The FINTEC workflow](26-the-fintec-workflow.md) · [28 · Common mistakes and recovery ➡️](28-common-mistakes-and-recovery.md)
