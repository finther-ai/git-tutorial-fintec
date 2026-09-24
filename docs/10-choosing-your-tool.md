# 10 · Choosing your tool: Web, Web IDE, Git terminal, or glab

> ⏱️ **~10 min** · 🎯 **Level: Beginner** · 🧰 **Tool needed: depends on your choice 🙂**

---

## The one-line summary

**There are four ways to work with GitLab at FINTEC — start with the browser, graduate to the terminal when (and only when) you need it.**

| | 🌐 **GitLab web** | 🖥️ **Web IDE** | ⌨️ **Git terminal** | 🦊 **`glab` CLI** |
|---|---|---|---|---|
| **What it is** | gitlab.com in your browser | A full editor *inside* gitlab.com | Git on your own computer | GitLab's official command-line tool |
| **Install needed** | ❌ none | ❌ none | ✅ Git | ✅ Git + glab |
| **Works offline?** | ❌ | ❌ | ✅ | ✅ (until you push) |
| **Best for** | Reading, issues, reviews, small fixes | Multi-file edits, quick dev work | Real development, anything serious | Automating MRs/issues, power users |
| **Beginner-friendly?** | ✅✅ | ✅✅ | 🤔 teach me slowly ([11](11-clone-a-project.md)–[18](18-pull.md)) | ❌ advanced ([Advanced · 02](advanced/02-glab-cli.md)) |

> 🎯 **FINTEC guidance:** nobody will force the terminal on you. If the web interface solves your task today — use it. The rest of the main path (guides 11–18) teaches the terminal at beginner speed, because developers will eventually need it.

## When to use which — decision table

| You want to… | Use | Guide |
|---|---|---|
| Read code, check an issue, review an MR | 🌐 Web | [03](03-sign-in-and-the-interface.md), [20](20-review-a-merge-request.md) |
| Fix a typo / update a doc file | 🌐 Web | [09 · Create and upload files](09-create-and-upload-files.md) |
| Edit several files for one small change | 🖥️ Web IDE | [09](09-create-and-upload-files.md) |
| Develop features / run the project on your machine | ⌨️ Git terminal | [11](11-clone-a-project.md)–[18](18-pull.md) |
| Run tests, use your own tools (IDE, Python, …) | ⌨️ Git terminal | — |
| Create MRs/issues from the terminal, script repetitive work | 🦊 glab | [Advanced · 02 · glab CLI](advanced/02-glab-cli.md) |

## Terminal path · one-time setup

Going the Git route? Do these **once per computer**:

### 1 · Install Git

Download for your OS from **[git-scm.com/downloads](https://git-scm.com/downloads)** (Windows: *Git for Windows* gives you "Git Bash", a friendly terminal). Check it works:

```bash
git --version
# → git version 2.x.something  ✅
```

### 2 · Tell Git who you are

Every commit is signed with your name and email — set them once:

```bash
git config --global user.name  "Siti Rahman"
git config --global user.email "siti@finther.my"
```

> ⚠️ Use your **real name** and your **FINTEC email** — these appear on every commit you make, in every project, forever.

### 3 · Understand the access-token rule 🎫

> ⚠️ **This surprises everyone:** GitLab **does not accept your GitLab account password** in the terminal. When Git asks for a password, it wants a **Personal Access Token (PAT)** — a long string that acts as a password for tools.

**Create one (once, ~2 minutes):**

1. GitLab (website) → avatar → **Edit profile**
2. Left menu → **Access tokens** → **Add new token** → *Personal access token*
3. **Token name:** `my-laptop` · **Expiration:** GitLab typically requires one (often up to a year) — set it and note the date
4. **Scopes:** tick `read_repository` and `write_repository`
5. **Create personal access token** → **copy the token immediately** (it's shown only once!)

That token is what you'll paste when Git asks for a password ([11 · Clone a project](11-clone-a-project.md) shows exactly where). Your computer can remember it for you — see the tip there.

> 🔐 Token hygiene: treat a PAT like a password. Never paste it into chats, tickets, or code. Expired? Create a new one, and revoke the old under **Edit profile → Access tokens**. More rules: [29 · Security basics](29-security-basics.md).

### 4 · (Optional now) install `glab`

Skip unless curious: [Advanced · 02 · glab CLI](advanced/02-glab-cli.md).

## Which guides teach which tool

- 🌐 Web: [08](08-create-a-project-from-scratch.md), [09](09-create-and-upload-files.md), [19](19-create-a-merge-request.md)–[23](23-issues.md)
- 🖥️ Web IDE: [09](09-create-and-upload-files.md), [22](22-fix-merge-conflicts.md)
- ⌨️ Git: [11](11-clone-a-project.md) → [18](18-pull.md)
- 🦊 glab: [Advanced · 02](advanced/02-glab-cli.md)

## ✅ Check yourself

1. Newest employee, needs to fix one typo. Tool? → *Web interface, pencil icon.*
2. Developer, builds the app daily. Tool? → *Git terminal (Web IDE occasionally, glab when comfortable).*
3. Git asks for a password — whose password? → *Neither — paste a Personal Access Token.*

---

[⬅️ 09 · Create and upload files](09-create-and-upload-files.md) · [11 · Clone a project ➡️](11-clone-a-project.md)
