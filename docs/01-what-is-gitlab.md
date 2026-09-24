# 01 · What is GitLab, and why does FINTEC use it?

> ⏱️ **~5 min** · 🎯 **Level: Absolute beginner** · 🧰 **Tool needed: none**

---

## The one-sentence answer

**GitLab is a website where FINTEC stores its project files, keeps the full history of every change, and lets the team work together without stepping on each other's toes.**

That's it. Everything else in this guide just unpacks that sentence.

## Think of it like this

Imagine your team writes documents together in one shared folder on someone's laptop:

- 📂 Only one person can open the laptop at a time
- 💥 Two people edit the same file → one version is silently lost
- 🕰️ Nobody knows what the document looked like last Tuesday
- 😰 The laptop dies → everything is gone

GitLab solves all four problems:

| Problem with the shared laptop | How GitLab fixes it |
|---|---|
| One laptop, one copy | Every team member has a **full copy** of the project on their own computer |
| Edits silently overwrite each other | Changes go through **Merge Requests** — proposed changes that get **reviewed** before they land |
| No history | Every change is a **commit** with an author, a date, and a message. You can go back to any point in time |
| Laptop dies | The master copy lives on **GitLab's servers**, backed up, not on anyone's laptop |

## Three words you'll see everywhere

Before you go further, learn these three plain-English definitions. The whole tutorial builds on them:

| Word | Plain English |
|---|---|
| **Repository** (or "repo") | The project's **file storage + full history**, all in one place. One project = one repository |
| **Commit** | A **saved snapshot** of your changes, with a short message describing what you did |
| **Merge Request** (MR) | A polite proposal: *"Here are my changes — please review them and add them to the main project"* |

> 📌 **Note:** You may have heard of **GitHub**. GitLab and GitHub are competitors with the same core idea. FINTEC chose GitLab. If you find tutorials online for GitHub, the concepts transfer almost 1-to-1 — just the buttons are in different places.

## Why FINTEC specifically uses it

- 🏦 **Everything in one place** — every project, its history, and its documentation live at one address: `https://gitlab.com/ai-fintec`
- 👀 **Review before release** — nothing reaches the main project unseen; every change passes through a Merge Request
- 🧾 **Built-in task tracking** — Issues let the team track tasks, bugs, and requests next to the code itself
- 🔐 **Access control** — people only get the level of access appropriate for their role (see [06 · Roles and permissions](06-roles-and-permissions.md))
- 🌐 **It's just a website** — you can do 80% of your daily work from the browser. No installations required (see [10 · Choosing your tool](10-choosing-your-tool.md))

## What you can do in GitLab

```
┌─────────────────────────────────────────────────────┐
│                     GITLAB                          │
│                                                     │
│  📁 Store project files (the repository)            │
│  🕰️  Keep the history of every change               │
│  🎫 Track tasks and bugs (Issues)                   │
│  🔀 Propose and review changes (Merge Requests)     │
│  👥 Control who can do what (roles & permissions)   │
│  📖 Host project documentation (README, wikis)      │
└─────────────────────────────────────────────────────┘
```

## ✅ Check yourself

You don't need to *do* anything in this guide. Just make sure you can answer:

1. What is a repository, in one sentence? → *The project's file storage and history.*
2. What is a commit? → *A saved snapshot of changes with a message.*
3. What is a Merge Request? → *A proposed change, waiting for review.*

If those three answers make sense, you're ready. 🎉

---

[⬅️ Back to the guide map](../README.md) · [02 · Create your GitLab account ➡️](02-create-your-gitlab-account.md)
