# 16 · Commits — saving snapshots that make sense

> ⏱️ **~8 min** · 🎯 **Level: Beginner** · 🧰 **Tool needed: Git terminal (or Web IDE)**

---

## Where you are in the loop

```
Issue → Branch → Work ✅ → **Commit** → Push → Merge Request → Review → Merge
```

You've made changes on your branch. A **commit** — a saved snapshot with a message — records them in the project's history ([12 · concepts](12-git-concepts-in-plain-english.md)).

## The three-step commit

```bash
git status                  # 1. WHAT changed? (read it — every time)
git add .                   # 2. stage the changes you want in this snapshot
git commit -m "…"           # 3. snapshot + one-line reason
```

Example from our running task (Issue #12, `loan-calculator`):

```bash
git status
#  modified:   calculator.js
#  modified:   index.html

git add .

git commit -m "Show total interest paid under the payment table"
# [12-show-total-interest a1b2c3d] Show total interest paid under the payment table
#  2 files changed, 14 insertions(+)
```

That last line is Git confirming: snapshot `a1b2c3d` saved **on your computer**. Nobody else can see it yet — that's push ([17](17-push.md)).

## Writing commit messages people actually thank you for

The formula:

```text
<imperative summary, ≤50 chars>        ← the subject line

(optional body: what & why, wrapped ~72 chars)
```

| ✅ Good | ❌ Avoid |
|---|---|
| `Show total interest paid under the payment table` | `update` · `changes` · `asdf` |
| `Fix NaN when loan amount is empty` | `fix bug` |
| `Add validation to loan amount input` | `final version` · `misc fixes` |

Three rules of thumb:

1. **Complete the sentence:** *"If applied, this commit will **…**"* — `Add validation…` ✅, `added validation…`/`validation` ❌
2. **Say why in the body when it's not obvious.** Multi-line message? `git commit` (no `-m`) opens an editor; first line = subject, blank line, then body.
3. **One commit = one logical change.** "Fix NaN bug + add footer logo" should be two commits: reviewers (and future you) can then understand each separately.

> 💡 `git log --oneline` shows your commits piling up — a nice little dopamine loop, and proof your history reads like a story.

## Commit early, commit often

- Commits are **local and private** — they're free. Take a snapshot whenever you reach a working state
- Small commits = easy reviews, easy rollbacks, easy "which change broke this?" hunts
- Never commit to *hide* untested garbage you plan to fix later — but do snapshot working states generously

## ⚠️ Before every commit: the 5-second secret scan

Did any changed file contain credentials — passwords, API keys, `.env`, tokens?

```bash
git status   # any file named .env, credentials, secret, key? 🚨
```

**Committed secrets are forever** (until rotated): even "deleting" a file in a later commit leaves it in history. Full drill, including what to do if it's too late: **[29 · Security basics](29-security-basics.md)**. *Read that guide before your first real commit — genuinely.*

## Variations you'll meet

| Command | When |
|---|---|
| `git add calculator.js` | Stage only one file — when changes are unrelated ([13](13-everyday-git-commands.md)) |
| `git restore --staged calculator.js` | Unstage: "oops, not this file yet" |
| `git commit --amend -m "better message"` | Fix the message of your **latest, un-pushed** commit ([28](28-common-mistakes-and-recovery.md)) |
| Commit panel in Web IDE / IDE Git button | Same mechanics, visual — the panel lists staged files and asks for a message |

## ✅ Check yourself

1. Does committing share your code with the team? → *No — local snapshot only; sharing happens at push.*
2. Rewrite into a good message: `fixed stuff`? → *`Fix monthly payment showing NaN when amount is empty`.*
3. Why scan for `.env`/keys before committing? → *Commits (and history) are forever; committed secrets must be rotated as if leaked.*

---

[⬅️ 15 · Making changes](15-making-changes.md) · [17 · Push ➡️](17-push.md)
