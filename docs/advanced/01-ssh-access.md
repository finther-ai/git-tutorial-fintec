# Advanced · 01 · SSH access to GitLab

> ⏱️ **~15 min** · 🎯 **Level: Optional — not needed for the beginner path** · 🧰 **Tool needed: terminal**

---

## Do you need this?

**Probably not yet.** The FINTEC beginner path deliberately uses **HTTPS + Personal Access Token** for everything ([10 · Choosing your tool](../10-choosing-your-tool.md)) — it works on every machine with zero setup beyond one token. Finish the main path first; come here when terminal Git feels routine.

**SSH replaces the token with a cryptographic key pair:** a private key that lives on your computer, and a public key registered with GitLab. Git then authenticates automatically — no password prompts, no expiring tokens.

| | HTTPS + token (beginner default) | SSH (this guide) |
|---|---|---|
| Setup | one token, 2 min | one-time, ~10 min |
| Auth prompts | token paste (or stored) | none, ever |
| Token expiry | yes — renew | no expiry |
| Cross-machine setup | trivial per machine | key per machine (don't copy private keys around!) |

## Set it up

### 1 · Generate a key pair

```bash
ssh-keygen -t ed25519 -C "siti@finther.my - work laptop"
```

- Press **Enter** to accept the default location (`~/.ssh/id_ed25519`)
- A **passphrase** is optional; recommended on shared machines. Empty passphrase = convenience, less protection — your call (and your lead's, on company hardware)

Two files appear:

```text
~/.ssh/id_ed25519      ← PRIVATE key. Never leaves this machine. Ever.
~/.ssh/id_ed25519.pub  ← PUBLIC key. This is what you give GitLab.
```

### 2 · Register the public key with GitLab

```bash
cat ~/.ssh/id_ed25519.pub        # select and copy the whole line
```

Then on GitLab: **avatar → Edit profile → SSH Keys → Add new key** → paste → name it (`work-laptop`) → optional expiry → **Add key**.

### 3 · Test

```bash
ssh -T git@gitlab.com
# → "Welcome to GitLab, @siti.rahman!"  ✅
```

## Use it

Clone URLs change shape:

```bash
# HTTPS (before)
git clone https://gitlab.com/ai-fintec/loan-calculator.git

# SSH (after)
git clone git@gitlab.com:ai-fintec/loan-calculator.git
```

Copy them from the same **`Code` ▾** button — it offers both tabs ([11 · Clone](../11-clone-a-project.md)).

**Existing clone, switch to SSH** (one command):

```bash
git remote set-url origin git@gitlab.com:ai-fintec/loan-calculator.git
git remote -v        # confirm
```

## Security rules (the whole guide in four lines)

1. The **private key never leaves the machine** — not in chat, not in a repo (see [29 · Security basics](../29-security-basics.md)), not on a flash drive
2. **One key per device** — revoke the dead laptop's key under *Edit profile → SSH Keys*
3. Public key = shareable; private key = organ 🫀
4. Lose the machine? Revoke its key on GitLab immediately

## 🚫 Troubleshooting

| Symptom | Fix |
|---|---|
| `Permission denied (publickey)` | Key not registered, or wrong key — redo step 2; check you're testing `git@gitlab.com` (not your username) |
| Works sometimes, not others | Multiple keys (`~/.ssh/config` needed) — beyond this guide; ask your lead |
| Cloned via HTTPS, prompts keep coming | You're still on HTTPS — that's fine! Use a token, or switch with `set-url` |

---

[⬅️ 30 · What do I do next?](../30-what-do-i-do-next.md) · [Advanced · 02 · glab CLI ➡️](02-glab-cli.md) · [🏠 Guide map](../../README.md)
