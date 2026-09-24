# 08 · Create a project from scratch

> ⏱️ **~10 min** · 🎯 **Level: Beginner** · 🧰 **Tool needed: a web browser + (usually) Maintainer/Owner rights**

---

## What you'll do

Create a brand-new project with its own repository, entirely in the browser. Our running example: FINTEC is starting a small web app called **`loan-calculator`** — estimates monthly loan repayments.

> 🔑 **Permission check:** creating a project **inside the `ai-fintec` group** requires at least **Maintainer** there (or the group allows Developers to create projects). If you can't, this is a "ask your team lead" moment — send them the project name and purpose, and they'll create it or grant you the rights. Practising in **your personal namespace** works with any account.

## Step by step

### 1 · Start the creation flow

Sign in → top bar → **➕ (New…)** → **New project/repository**.

You'll see several cards:

| Card | When to pick it |
|---|---|
| **Create blank project** | ✅ 99% of the time — this guide |
| **Create from template** | GitLab ships starter templates; nice for specific tech, adds clutter for beginners |
| **Import project** | Moving an existing repo from GitHub/elsewhere — ask your lead first |

### 2 · Fill in the form

| Field | What to enter | Our example |
|---|---|---|
| **Project name** | Human-friendly name (spaces allowed here) | `Loan Calculator` |
| **Project URL** | Keep the group prefix `ai-fintec/` — **not** your personal namespace. The slug auto-fills from the name | `ai-fintec/loan-calculator` |
| **Description** | One sentence a stranger understands | `Estimates monthly loan repayments for FINTEC customers.` |
| **Visibility Level** | 🔒 **Private** for real FINTEC work — see [05 · Create or join a project](05-create-or-join-a-project.md) | Private |
| **Initialize repository with a README** | ✅ **Tick this.** Without it the project is an empty husk and harder to clone | ✅ |

> 💡 **Why tick "Initialize with a README"?** An empty repository has no `main` branch yet, so cloning it and opening Merge Requests gets awkward. The README gives the project a starting commit and a front page. You'll write a proper one in [25 · READMEs and documentation](25-readme-and-documentation.md).

Optional settings you can safely ignore for now: project tagging, avatar, and everything under *Advanced*. You can change all of it later under **Settings → General**.

### 3 · Create it

Click **Create project**. 🎉

You land on your project page: a file list containing `README.md`, rendered as the front page.

### 4 · The 60-second setup checklist

Do these right after creating (each has its own guide):

- [ ] **Write the README** so the front page explains the project → [25](25-readme-and-documentation.md)
- [ ] **Add members** — left sidebar → **Manage → Members → Invite members** → pick role ([06 · Roles and permissions](06-roles-and-permissions.md))
- [ ] **Plan the first Issue** → [23 · Issues](23-issues.md)

> 💡 **Recommended housekeeping (not official policy):** under **Settings → General → Visibility**, double-check *Project visibility* is Private, and consider removing features you won't use (e.g. wikis, packages) to keep the sidebar clean.

## Creating in your personal namespace (for practice)

Identical steps — just **don't change the project URL prefix** from your own username. Perfect for following the rest of this tutorial safely. Remember: at FINTEC, real work belongs in the group ([04 · Groups, projects & repositories](04-groups-projects-and-repositories.md)).

## 🚫 Common problems

| Problem | Fix |
|---|---|
| The group `ai-fintec` isn't offered in the URL | You lack creation rights in the group → ask a Maintainer |
| "Name has already been taken" | The slug exists in that group — pick another name or rename the old project |
| Project created without README | It's fixable: use the web editor to add `README.md` → [09 · Create and upload files](09-create-and-upload-files.md) |
| Wrong visibility level | **Settings → General → Visibility → Change visibility** |

## ✅ Done when…

- [x] `https://gitlab.com/ai-fintec/<your-project>` opens
- [x] The file list shows `README.md`
- [x] Your teammates can see it (or you know whom to ask)

---

[⬅️ 07 · How FINTEC organizes projects](07-how-fintec-organizes-projects.md) · [09 · Create and upload files ➡️](09-create-and-upload-files.md)
