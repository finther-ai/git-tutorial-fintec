# 23 · Issues — tasks, bugs, and requests

> ⏱️ **~10 min** · 🎯 **Level: Beginner** · 🧰 **Tool needed: web browser**

---

## What an Issue is

**An Issue is one item of work, tracked inside the project instead of in someone's chat history:** a task, a bug, or a request. Every Issue gets a **number** (`#12`, `#17`…) that the whole project can point to — which is exactly what makes the FINTEC workflow chain possible:

```
Issue #12 → Branch 12-… → Merge Request ("Closes #12") → Merge → Issue auto-closed ✅
```

If work isn't an Issue, it doesn't exist: no record, no link to the code that solved it, no way to say *done*.

## Open the Issues list

Project → left sidebar → **Plan → Issues**. You'll see the list with status (Open/Closed), assignee, and labels. This list *is* the project's to-do board.

## Creating an Issue

Click **New issue**. What matters:

| Field | Guidance | Example (loan-calculator) |
|---|---|---|
| **Title** | One line a teammate instantly understands | `Monthly payment shows RM NaN when amount is empty` |
| **Description** | Details, steps, expectations — below | see below |
| **Assignee** | Who's doing it (usually *you*, after claiming) | `Siti` |
| **Label** | Team-wide categories if the project has them | `bug`, `feature`, `documentation` |
| **Milestone / Due date / Weight** | Ignore unless your team uses them | — |

### Description patterns that work

**🐞 Bug report:**

```markdown
**What happens:** Enter a loan amount, clear the field → payment shows "RM NaN".

**Expected:** shows "—" (no value) instead of NaN.

**Steps to reproduce:**
1. Open the calculator
2. Type 20000 in amount, then delete it
3. Monthly payment reads "RM NaN"

Screenshot attached. Browser: Safari 18.
```

**✨ Feature request / task:**

```markdown
**Goal:** show the total interest paid over the loan lifetime, under the payment table.

**Why:** customers only see the monthly instalment and ask support "what am I actually paying overall?"

**Notes:** labelled `feature`; data is already computable from existing inputs (see #17 for the NaN bug affecting the same panel).
```

See what those have in common? **A stranger can act on them without asking a single clarifying question.** Write for that stranger — they're future you.

## Living with Issues — the daily moves

| Move | How |
|---|---|
| Claim work | Open an unassigned Issue → set **Assignee: yourself** (don't silently start on someone's item) |
| Comment | Anything worth saying goes *in the Issue* — decisions made in chat get pasted back: *"Agreed in standup: we'll cap the term at 30 years"* |
| Cross-reference | Type `#17` anywhere → GitLab turns it into a live link between the two Issues |
| Track the sprint | **Plan → Boards** if the project uses boards — Issues as draggable cards, very satisfying |
| Close it | The **Close issue** button — or, the elegant way: an MR whose description says `Closes #12` ([24 · Linking](24-link-issues-branches-merge-requests.md)) |

## Who opens Issues? (everyone.)

- **You** — found a bug? Missed doc? Vague feeling something's wrong? **Open an Issue.** A one-line issue today beats a forgotten annoyance next month
- **Your reporter/analyst teammates** — requests and bugs from the business side usually arrive as Issues they file
- **Reviewers** — "this MR also needs X" → Issue it, don't bury it in review comments ([20 · Reviewing](20-review-a-merge-request.md))

> 💡 **Recommended etiquette (team practice, not official policy):** before opening, search existing Issues — a duplicate with extra detail is still useful (comment there); a blind duplicate is noise. Keep one Issue = one problem: two bugs get two Issues.

## From Issue → to actual work

That's the hinge of the whole FINTEC workflow — creating the branch from the Issue and linking everything automatically:

👉 **[24 · Linking Issues, Branches and Merge Requests](24-link-issues-branches-merge-requests.md)** — the shortest guide in this tutorial and the one that ties all the previous ones together.

## 🚫 Common problems

| Problem | Fix |
|---|---|
| Can't see **Plan → Issues** in the sidebar | You're probably not inside a project page (or your role is too low — [06 · Roles](06-roles-and-permissions.md)) |
| Opened an Issue and nobody reacted | Assign it to the right person, or raise it in standup — Issues don't page anyone by themselves 🙂 |
| Issue numbers don't match (`#12` vs `!13`) | Normal: Issues are `#n`, Merge Requests are `!n` — two separate counters |

## ✅ Check yourself

1. What is an Issue, one sentence? → *One tracked item of work — task, bug, or request — with a number the project can link to.*
2. Work agreed in a chat — where does the decision land? → *Pasted into the Issue; chat is not project memory.*
3. How does work normally *close* an Issue? → *An MR saying `Closes #<n>` — on merge, the Issue closes itself.*

---

[⬅️ 22 · Fix merge conflicts](22-fix-merge-conflicts.md) · [24 · Linking Issues, Branches and Merge Requests ➡️](24-link-issues-branches-merge-requests.md)
