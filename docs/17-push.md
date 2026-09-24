# 17 · Push — share your work with GitLab

> ⏱️ **~7 min** · 🎯 **Level: Beginner** · 🧰 **Tool needed: Git terminal**

---

## Where you are in the loop

```
Issue → Branch → Work → Commit ✅ → **Push** → Merge Request → Review → Merge
```

Your commits live on your computer. **Push uploads them to GitLab.** Until you push, your work is invisible — a laptop loss away from gone. Push early, push often.

## First push of a branch

```bash
git push -u origin 12-show-total-interest
```

Breaking it down:

| Piece | Meaning |
|---|---|
| `git push` | upload my commits |
| `origin` | the nickname for *the GitLab copy of this project* (created automatically when you cloned — [11](11-clone-a-project.md)) |
| `12-show-total-interest` | which branch to upload |
| `-u` | *"remember this pairing"* — links your local branch to the GitLab branch, **once** |

GitLab answers with a friendly link:

```text
remote: To create a merge request for 12-show-total-interest, visit:
remote:   https://gitlab.com/ai-fintec/loan-calculator/-/merge_requests/new?merge_request[source_branch]=12-show-total-interest
```

That's your next step: **[19 · Create a Merge Request](19-create-a-merge-request.md)** — click it while GitLab is offering. 🙂

## Every push after that

```bash
git push
```

That's all — the `-u` did its job. Onwards.

## What happens during a push

1. Git asks *GitLab*: "anything new on this branch?"
2. No → your commits upload; the GitLab branch now matches yours
3. Yes (a teammate pushed something) → Git refuses with `! [rejected]` — **not an error, a protection.** It wants you to `git pull` first ([18 · Pull](18-pull.md)), so both sets of changes combine properly

> ⚠️ **Never "fix" a rejected push with `--force`.** Force-push overwrites the shared branch and *deletes* teammates' commits. On protected branches like `main` GitLab blocks it anyway. The correct move is always: pull → resolve → push ([28 · Common mistakes](28-common-mistakes-and-recovery.md)).

## Authentication reminder

First push (or after your token expired) Git asks:

```text
Username: siti.rahman
Password: █  ← paste your Personal Access Token, NOT your GitLab password
```

Token setup if you don't have one: [10 · Choosing your tool](10-choosing-your-tool.md). Storing it so Git stops asking: [11 · Clone](11-clone-a-project.md).

## Push etiquette at FINTEC

| Do | Don't |
|---|---|
| Push your branch whenever you reach a working state | Push straight to `main` — you can't; it's protected ([06](06-roles-and-permissions.md), [14](14-branches.md)) |
| Push before going home — it's your backup 🌙 | Push half-broken work onto a branch *someone else shares* without a heads-up |
| Push after every finished sub-task | Rewrite pushed commits (`--amend` on pushed work, `--force`) — [28](28-common-mistakes-and-recovery.md) |

## 🚫 Common problems

| Problem | Fix |
|---|---|
| `Authentication failed` | You used your password → use your **access token** ([10](10-choosing-your-tool.md)) |
| `! [rejected] … fetch first` | Normal: `git pull` → resolve conflicts if any ([22](22-fix-merge-conflicts.md)) → `git push` again |
| `error: failed to push some refs` / `protected branch hook declined` | You're trying to push to `main` (or another protected branch) → push *your branch* instead and open an MR ([19](19-create-a-merge-request.md)) |
| `Everything up-to-date` but GitLab shows nothing | You're pushing while on the wrong branch — `git status` first 🙂 |

## ✅ Check yourself

1. What does `-u` do, and how often do you need it? → *Links local branch ↔ GitLab branch; once per branch.*
2. Push was rejected — what's the correct response? → *`git pull` first, resolve if needed, push again. Never force.*
3. Can you push directly to `main`? → *No — protected. Your branch + Merge Request is the path.*

---

[⬅️ 16 · Commits](16-commits.md) · [18 · Pull ➡️](18-pull.md)
