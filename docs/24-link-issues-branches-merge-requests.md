# 24 · Linking Issues → Branches → Merge Requests

> ⏱️ **~8 min** · 🎯 **Level: Beginner** · 🧰 **Tool needed: web browser or terminal**

---

## The connective tissue of the FINTEC workflow

Individually you know all three pieces — [23 · Issues](23-issues.md), [14 · Branches](14-branches.md), [19 · Merge Requests](19-create-a-merge-request.md). This guide connects them so the project *tells its own story*:

```
Issue #12  ──branch named──▶  12-show-total-interest  ──MR says──▶  "Closes #12"
    ▲                                                                    │
    └────────────── auto-closed on merge ◀── Merge ◀── Review ───────────┘
```

**Why bother linking?** Open any merged MR months later and you instantly see *which task* it solved, *who agreed*, *what was discussed*. Unlinked work is archaeology; linked work is a story. Also: the Issue **closes itself**.

## The one-click version ✨ (learn this one)

1. Open the Issue (e.g. `#12`)
2. Click **Create merge request** (button on the Issue page)
3. GitLab creates — in one shot:
   - a **branch** named `12-show-total-interest` ✅
   - a **Draft Merge Request** *from that branch*, with `Closes #12` pre-filled in the description ✅
4. You do the work on that branch ([15](15-making-changes.md)), commit ([16](16-commits.md)), push ([17](17-push.md)) — the MR updates itself
5. Review ([20](20-review-a-merge-request.md)) → **Merge** ([21](21-approve-and-merge.md))
6. **Issue #12 closes automatically.** 🎉 Nothing to remember.

> 📌 If you already made the branch yourself, the button changes to something like *Create merge request* with your branch pre-selected — same result.

## The manual words (when you type things yourself)

GitLab reads certain **keywords + issue number** in the MR **description** (not the title, not comments):

| You write | Effect on merge |
|---|---|
| `Closes #12` | Issue #12 closes ✅ |
| `Fixes #12` | same |
| `Resolves #12` | same |
| `Closes #12, #14` | both close ✅ |
| `Relates to #12` / `See #12` | just a link — Issue **stays open** (deliberate!) |
| `Closes group/project#12` | cross-project closing — rare, but it exists |

**Details that matter:**

- Must be in the **description** of the MR
- Auto-close only fires when the MR targets the **default branch** (`main`)
- Typo'd it after creating? Edit the description — the link updates live

## Naming branches to link them (the convention)

The `12-` prefix isn't decoration — GitLab uses it to **suggest and associate** ([14 · naming](14-branches.md)):

```text
#12 → 12-show-total-interest     ✅ linked, filterable, self-explaining
#12 → my-branch                  ❌ story lost
```

Note the direction: the *branch name prefix* is convention (visual association); the *`Closes #12` keyword* is mechanism (actual automation). Use both.

## What the links look like when it's done right

- **On the Issue page:** the linked MR appears in the issue's *Related merge requests*; after merge the issue shows *Closed via merge request !13* with a direct link
- **On the MR page:** `Closes #12` renders as a live link to the issue
- **In the history:** every commit mentions its branch; every branch traces to its issue → the full *why* is one click from any line of code

## A worked mini-story

1. **Monday** — Issue #17 opened: `Monthly payment shows RM NaN when amount is empty` ([23](23-issues.md))
2. Siti clicks **Create merge request** → branch `17-fix-safari-nan-bug`, Draft MR auto-made with `Closes #17`
3. **Tuesday** — she fixes, commits twice with clear messages ([16](16-commits.md)), pushes ([17](17-push.md)); the Draft MR fills up with her commits
4. **Wednesday** — Ahmad reviews ([20](20-review-a-merge-request.md)), one `Nit:`, one ✅ Approve
5. **Wednesday 15:04** — Ahmad clicks **Merge** ([21](21-approve-and-merge.md))
6. Branch deleted · `main` updated · **Issue #17 closes itself**, stamped *"Closed via merge request !21"* — and the whole trail exists forever, for free

That chain — every step traceable, nothing remembered in someone's head — is what FINTEC's workflow buys you. Learn it once ([26 · The FINTEC workflow](26-the-fintec-workflow.md)), run it forever.

## 🚫 Common problems

| Problem | Fix |
|---|---|
| Merged, issue still open | Keyword missing/typo'd in the **description** → add `Closes #12`, or close manually — happens to everyone once |
| `Create merge request` button missing on the Issue | An MR already exists for that issue (linked!) — the issue page shows it |
| Accidentally typed `Closes #12` but didn't mean to close | Change it to `Relates to #12` before merge; after merge, reopen the issue manually |
| Two MRs both say `Closes #12` | Second one to merge finds the issue already closed — GitLab notes it. Harmless; tidy up the description |

## ✅ Check yourself

1. The three link mechanisms? → *Branch named `12-…` (convention) · MR description `Closes #12` (automation) · auto-close on merge to `main`.*
2. Which words close vs. only link? → *`Closes/Fixes/Resolves #n` close; `Relates to #n` only links.*
3. Fastest correct setup for a new task? → *Issue → Create merge request button → work on the branch it made.*

---

[⬅️ 23 · Issues](23-issues.md) · [25 · READMEs and documentation ➡️](25-readme-and-documentation.md)
