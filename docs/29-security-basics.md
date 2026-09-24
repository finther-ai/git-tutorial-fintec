# 29 · Security basics — passwords, tokens, secrets, and `.env`

> ⚠️ **The one guide where "oops" can cost real money.** Finance company. Read it once properly, then let the habits run.

> ⏱️ **~10 min** · 🎯 **Level: Everyone — no exceptions** · 🧰 **Tool needed: none**

---

## The one rule

> ## 🔑 If a value is meant to be secret, it never enters a commit. Ever. Not once, "temporarily", "just for testing", nothing.

Everything below is this rule, applied.

## Why Git makes this unforgiving

A commit is **forever**. Even this:

```bash
git commit -m "Add config"      # contains the API key 😬
git commit -m "Remove key"      # removes it from the files…
```

…keeps the key in **history**. Anyone with repo access (`git log`, or browsing old versions) can read it back like it never left. Add that GitLab copies repositories to every collaborator, backups, and forks, and the picture is clear: **once pushed, treat the secret as public — the only real fix is changing the secret.**

## The usual suspects 🕵️

| Leak | What it opens | Where it sneaks in |
|---|---|---|
| `.env` files | database passwords, API keys, service credentials | "I'll just commit my config so it deploys" |
| API keys / tokens in code | payment gateways, SMS, AI services | hard-coded `const API_KEY = "sk-…"` for convenience |
| Database passwords | the whole data layer | connection strings in `config.js`, `settings.py` |
| **GitLab Personal Access Tokens** | *your* GitLab identity — code, everything | pasted into scripts, or worse, committed |
| SSH private keys (`id_rsa`, `id_ed25519`) | everything those keys touch | copied "temporarily" into a project folder |
| Credentials in logs & screenshots | same as their source | pasted into Issues, MR comments, READMEs |

## The `.env` pattern (learn this now)

**Code and configuration are separated:**

```bash
# .env  ← holds secrets — NEVER committed
DATABASE_URL=postgres://user:secret@db.host:5432/prod
PAYMENT_API_KEY=sk_live_51H8x…
```

```js
// config.js  ← reads the secrets from the environment — safe to commit
const apiKey = process.env.PAYMENT_API_KEY;
```

And Git is told to ignore the file — project root, a file named exactly `.gitignore`:

```gitignore
# .gitignore — never track these
.env
.env.*
*.pem
*.key
```

> 💡 `.gitignore` is committed (it's not a secret — it's the *guardrail*). Most frameworks' starter templates ship a sensible one — keep it. New ignore line needed? It goes in through an MR like any change ([14 → 19](14-branches.md)).

> 📌 *Where do `.env` values live instead, if not in the repo?* Your machine locally; the deploy platform's secret store in production; a team password manager for sharing. **Where exactly is a FINTEC decision — ask your lead.** (This tutorial doesn't invent that policy; it just refuses to put them in Git.)

## Personal Access Tokens: your GitLab keys 🎫

You already use a PAT for terminal auth ([10 · Choosing your tool](10-choosing-your-tool.md)). Handle it like a house key:

- ✅ **Do:** give it the smallest scopes that work (`read_repository`, `write_repository` — not `api` "just in case"); set an expiry; one token per device
- 🚫 **Don't:** paste it in chat, email, Issues, code, screenshots — or commit it in a `.env` (see above: it's a secret like any other)
- 🔄 **Rotate:** expired/possibly exposed → **Edit profile → Access tokens** → create new, **revoke old**

Forgot where a token went? `Edit profile → Access tokens` shows *last used* dates. A token unused for a month gets revoked. Hygiene, not paranoia.

## Other habits that matter

- **Passwords:** unique per service, in a password manager — including your GitLab account ([02 · 2FA](02-create-your-gitlab-account.md) — recommended there, worth repeating here)
- **Screenshots for Issues:** crop out tokens, account numbers, customer data — bug reports leak more than bugs ([23 · Issues](23-issues.md))
- **Test/demo data:** fake names, fake balances — never customer data in a repo
- **Dependencies:** install from official sources only; a "helpful" pasted `npm install` line from the internet gets the same skepticism as everything else

## 🚨 "I already committed a secret." — the drill

**Minute one — assume leaked:**

1. **Revoke / rotate the credential.** Not after cleanup. **First.** (A leaked payment key being *cleaned from history* helps nobody if it's still active.)
2. **Tell your Maintainer/team lead** — today. Everyone does this once; a fast report is professionalism, silence is the actual career risk.

**Then, with your lead, clean up:**

- If it never left your machine (un-pushed): rewrite the local history — `git commit --amend` for the last commit ([28 · #2](28-common-mistakes-and-recovery.md)); ask your lead before anything fancier
- If it was pushed: removal from history needs history-rewriting tools — a Maintainer job with coordination, which is one more reason rotation came first

> 💡 *Bonus:* some GitLab plans can automatically **block pushes that contain known secret patterns** ("secret push protection"). If your project has it in **Settings → Repository**, leave it on — it will embarrass you briefly and save you thoroughly.

## The 5-second pre-commit scan (from [16 · Commits](16-commits.md), now with feeling)

```bash
git status && git diff
# 🚨 stop if you see: .env · key · secret · token · password · sk_live · BEGIN PRIVATE KEY
```

Ten seconds, before every commit, forever. That habit *is* this entire guide.

## ✅ Check yourself

1. Why is "I removed it in the next commit" not a fix? → *History keeps every version — the secret is still readable.*
2. Real fix for a leaked key? → *Revoke/rotate first, then report, then clean up.*
3. Where do secrets live instead of the repo? → *Local `.env` (git-ignored), platform secret stores, team password manager — ask your lead for FINTEC's setup.*

---

[⬅️ 28 · Common mistakes and recovery](28-common-mistakes-and-recovery.md) · [30 · What do I do next? ➡️](30-what-do-i-do-next.md)
