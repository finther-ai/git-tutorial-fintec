# 11 · Clone a project onto your computer

> ⏱️ **~10 min** · 🎯 **Level: Beginner · first terminal guide** · 🧰 **Tool needed: Git installed** ([10 · setup](10-choosing-your-tool.md))

---

## What "clone" means

**Clone = download a full copy of the project — every file *and* its entire history — onto your computer, connected back to GitLab.**

Not just a download: your copy **stays linked** to GitLab, so later you can *pull* others' changes down ([18](18-pull.md)) and *push* your work up ([17](17-push.md)).

```
   GitLab (ai-fintec/loan-calculator)          YOUR COMPUTER
  ┌───────────────────────────────┐    git clone   ┌─────────────────┐
  │  files + full history  🗄️     │  ───────────▶  │  your copy 📁   │
  └───────────────────────────────┘    one-time     └────────┬────────┘
             ▲                                          git pull│git push
             └─────────────────────── stays linked ─────────────┘
```

## Step by step (HTTPS — the FINTEC beginner way)

> 📌 We use **HTTPS** clone URLs — simple and beginner-friendly. (SSH is an optional alternative, deliberately not the default here: [Advanced · 01 · SSH access](advanced/01-ssh-access.md).)

### 1 · Copy the clone link

1. Open the project on GitLab
2. Click the blue **`Code` ▾** button
3. Under **Clone with HTTPS**, click the **copy icon** 📋
   → you now have something like `https://gitlab.com/ai-fintec/loan-calculator.git`

### 2 · Choose where it should live, in the terminal

Open a terminal (Windows: **Git Bash** from Git for Windows) and go to the folder where you keep work, e.g.:

```bash
cd ~/Documents/work      # macOS / Linux, or
cd /c/Users/siti/Documents/work   # Git Bash on Windows
```

### 3 · Clone

```bash
git clone https://gitlab.com/ai-fintec/loan-calculator.git
```

### 4 · Answer the login prompt (first time only)

Git asks:

```text
Username for 'https://gitlab.com': siti.rahman
Password for 'https://siti.rahman@gitlab.com':
```

- **Username** → your GitLab username
- **Password** → 🔑 **paste your Personal Access Token** — *not* your GitLab password (created in [10 · Choosing your tool](10-choosing-your-tool.md); no token? That guide shows the 2-minute setup)

> 💡 **Make your computer remember the token** (recommended — do it right after cloning succeeds):
> ```bash
> git config --global credential.helper store
> ```
> The *next* time you authenticate, Git saves the token and stops asking. (Stored in plain text in your home folder — acceptable on a personal work machine; if that bothers you, Git Credential Manager or `glab auth login` are nicer: [Advanced · 02](advanced/02-glab-cli.md).)

### 5 · Look around

```bash
cd loan-calculator
ls                  # see the files
git log --oneline   # see the history you downloaded
```

Full command tour next: [12 · Git concepts](12-git-concepts-in-plain-english.md) and [13 · Everyday Git commands](13-everyday-git-commands.md).

## What you got

```
loan-calculator/
├── .git/          ← hidden: the entire history (don't touch, don't delete)
├── README.md      ← the project front page
└── …project files
```

- The `.git/` folder *is* the history — deleting it turns your connected clone into a dumb folder copy
- Everything in here is yours to work on safely — GitLab holds the master copy

## 🚫 Common problems

| Problem | Fix |
|---|---|
| `Authentication failed` | You typed your GitLab **password**. Use the **access token** ([10](10-choosing-your-tool.md)) |
| `remote: HTTP Basic: Access denied. … expired` | Your PAT expired → create a new one ([10](10-choosing-your-tool.md)) |
| `fatal: repository … not found` | Typo in the URL, project is private and you're not a member ([05](05-create-or-join-a-project.md)), or you're outside the group URL — copy the link again with the `Code` ▾ button |
| Cloned into the wrong place | Just delete the folder and re-run `git clone` where you meant to. Harmless |
| `git: command not found` | Git isn't installed / terminal doesn't see it → [10 · install Git](10-choosing-your-tool.md) |

## Web alternative (no terminal at all)

Just need the files, not the history? **`Code` ▾ → Download** this repository → a ZIP. Fine for a look, but you can't pull/push — for real work, clone.

## ✅ Done when…

- [x] `git clone …` finished with no red errors
- [x] `cd loan-calculator && git log --oneline` shows at least one commit

---

[⬅️ 10 · Choosing your tool](10-choosing-your-tool.md) · [12 · Git concepts in plain English ➡️](12-git-concepts-in-plain-english.md)
