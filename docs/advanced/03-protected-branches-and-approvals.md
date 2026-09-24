# Advanced · 03 · Protected branches & MR approvals (for Maintainers)

> ⏱️ **~10 min** · 🎯 **Level: Optional — Maintainer material** · 🧰 **Tool needed: web browser (Maintainer role)**

---

## Why this exists

Every beginner guide here mentions *"main is protected"* ([06 · Roles](../06-roles-and-permissions.md), [14 · Branches](../14-branches.md)) and *"approvals may be required"* ([21 · Approve and merge](../21-approve-and-merge.md)). **This guide is for the Maintainers who configure that** — so the team's guardrails are deliberate, not accident.

> 🏢 **Policy honesty:** GitLab ships sensible defaults, shown below. What FINTEC *requires* per project is a team-lead decision — this guide explains the dials, not company law.

## Protected branches

**A protected branch = selected roles may push; nobody may force-push; merging follows your rules.** `main` is protected by default when a project is created — that's why Developers get *"rejected · protected branch hook"* ([17 · Push](../17-push.md)).

### Where

Project → **Settings → Repository** → expand **Protected branches**

### The dials

| Setting | Meaning | Sensible beginner-team value |
|---|---|---|
| **Allowed to merge** | who can land code here | Maintainers |
| **Allowed to push and merge** | who can commit directly | Maintainers (i.e. nobody bypasses MRs) |
| **Allowed to force push** | rewrite history | ❌ off. Always off. ([28 · recovery](../28-common-mistakes-and-recovery.md) explains the pain this prevents) |
| **Code owner approval** | require sign-off from declared code owners | optional — needs a `CODEOWNERS` file (below) |

Defaults on a fresh project: *Maintainers may push & merge, force push off.* For most small FINTEC teams, **change nothing** — the defaults are exactly the beginner-path assumptions. Revisit when a second team shares the repo.

### What it feels like from the team's side

- Developer pushes to `main` → rejected with a clear message → they use a branch + MR ([14](../14-branches.md)) — *the protection teaching the workflow for you*
- Maintainer pushes directly to `main` → allowed, but consider whether you're modelling the habit you want 🙂
- MR targeting `main` follows the approval rules below

## Merge request approvals

**Approvals = "N distinct people must press Approve before Merge unlocks"** ([20 → 21](../20-review-a-merge-request.md)).

### Where

Project → **Settings → Merge requests** → expand **Merge request approvals**

### The dials

| Setting | Meaning | Sensible beginner-team value |
|---|---|---|
| **Approvals required** | minimum approvals to merge | `1` for small teams — enough for the review habit without creating queues |
| **Eligible approvers** | whose approvals count | Developers + Maintainers (defaults are fine) |
| **Prevent author approval** | can the author approve their own MR? | keep blocked — *someone else's eyes* is the point ([20](../20-review-a-merge-request.md)) |
| **Prevent merge request author from merging** | self-merge lock | blocked, ideally — the workflow's integrity ([26](../26-the-fintec-workflow.md)) |

Other toggles on the same settings page worth knowing (defaults usually fine):

- **Merge checks** — e.g. *"All threads resolved"* / *"Pipelines must succeed"* before merge. Pipelines only matter once the project has CI (an *advanced* topic beyond this tutorial — ask your lead if/when it applies)
- **Squash default** — whether Merge folds commits into one ([21 · options](../21-approve-and-merge.md)). Team taste; just pick one and stay consistent
- **Merge trains / auto-merge** — powerful queueing for busy repos; ignore until MR volume demands it

## CODEOWNERS — routing reviews automatically

A small file in the repo that declares *"this path's reviews go to these people"*. Location: `CODEOWNERS`, `docs/CODEOWNERS`, or `.gitlab/CODEOWNERS`:

```text
# entries: <path pattern>   <@user or @group>
*                       @ahmad.lee
/docs/                  @meiling.tan
/payments/              @ahmad.lee @siti.rahman
```

With *"Code owner approval"* enabled on a protected branch, changes under those paths **require that person's approval** — review requests route themselves. Start simple (`*` → the lead); grow it when ownership genuinely splits.

## A Maintainer's 10-minute health check

Run this on any project you inherit:

- [ ] **Settings → Repository → Protected branches:** `main` protected · force push **off**
- [ ] **Settings → Merge requests:** approvals ≥ 1 · author can't approve/merge own MR
- [ ] **Settings → General → Visibility:** Private for real FINTEC work ([05](../05-create-or-join-a-project.md))
- [ ] **Manage → Members:** roles match reality — lowest role that does the job ([06](../06-roles-and-permissions.md)); leavers removed
- [ ] **Settings → Repository:** secret push protection on, if your plan has it ([29 · Security](../29-security-basics.md))
- [ ] README passes the 60-second test ([25](../25-readme-and-documentation.md))

That checklist is most of "good project hygiene" in practice. Pass it on to the next Maintainer.

## 🚫 Troubleshooting

| Symptom | Where to look |
|---|---|
| Team flooded with "can you merge this?" | Approvals config vs. who actually merges — make the Maintainer rotation explicit |
| "Pipeline must succeed" blocks everything, no CI exists | A merge check enabled with nothing to satisfy it — Settings → Merge requests |
| Developer *should* merge but can't | Eligible approvers / role too low — decide deliberately, don't just promote reflexively |
| Protection feels like bureaucracy | It's guarding `main`, the one branch everyone builds on — loosen *deliberately*, never in a hurry |

---

[⬅️ Advanced · 02 · glab CLI](02-glab-cli.md) · [Advanced · 04 · Git power moves ➡️](04-git-power-moves.md)
