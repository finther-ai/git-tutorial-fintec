# 06 · Roles and permissions

> ⏱️ **~7 min** · 🎯 **Level: Beginner** · 🧰 **Tool needed: a web browser**

---

## The idea in one sentence

**Your role decides what you can do in a project — and everyone at FINTEC should know which role they have, so you know what to expect from yourself and whom to ask for the rest.**

## The five roles

Roles are assigned per project (or for the whole group). From least to most powerful:

| Role | Plain English | Typical FINTEC example |
|---|---|---|
| **Guest** | Can look at issues and open new ones — no code access in private projects | An external consultant who only needs to file requests |
| **Reporter** | Can read everything and manage issues, but **cannot change the code** | A business analyst reading code, managing the task list, writing reports |
| **Developer** | The working role: create branches, push code, open and be assigned Merge Requests | A developer or data analyst doing day-to-day work |
| **Maintainer** | Team lead level: everything a Developer does **plus** merge code, manage settings, add members, push to protected branches | A senior engineer or team lead reviewing and merging work |
| **Owner** | Group-level boss: manage the group, create projects, admin members across projects | Head of engineering, group admin |

## The simplified permission table

What matters day-to-day:

| Action | Guest | Reporter | Developer | Maintainer |
|---|:-:|:-:|:-:|:-:|
| View code in a private project | — | ✅ | ✅ | ✅ |
| Create / comment on issues | ✅ | ✅ | ✅ | ✅ |
| Work on Merge Requests (branch → push → MR) | — | — | ✅ | ✅ |
| **Merge** a Merge Request | — | — | ⚠️* | ✅ |
| Push directly to protected branches (e.g. `main`) | — | — | — | ✅ |
| Manage project settings and members | — | — | — | ✅ |

\* *Whether a Developer can merge depends on each project's approval settings — many teams require a Maintainer (or a set number of approvals) to press the final Merge button. See [21 · Approve and merge](21-approve-and-merge.md).*

> 📖 The full, exact permission matrix lives in GitLab's official docs: [Project and group roles and permissions](https://docs.gitlab.com/user/permissions/). Don't memorize it — just know it exists.

## How do I check my own role?

1. Open the project
2. Left sidebar → **Manage → Members**
3. Find yourself → read the **Role** column

If the menu says you're not allowed to view members, you're likely a Guest/Reporter or the list is restricted — just ask your team lead.

## What this means for you, practically

- **You're a Developer (most common):** your daily loop is *Issue → Branch → Work → Commit → Push → Merge Request → wait for review* ([26 · The FINTEC workflow](26-the-fintec-workflow.md)). You normally **cannot push directly to `main`** — and that's a feature, not an insult. `main` is protected.
- **You're a Reporter:** GitLab still has tons of value for you: issues, boards, documentation, and reviewing Merge Requests as a reader.
- **You're a Maintainer:** congratulations, you now also unblock everyone else. Be responsive to access requests. 🙂

> 💡 **Principle (recommended, not an official FINTEC policy):** give people the *lowest* role that lets them do their job, and raise it when they prove they need more. Easy to promote, awkward to demote.

## ✅ Check yourself

1. You can't push to `main` — broken account? → *No. `main` is protected; work happens on branches + Merge Requests.*
2. Who can add a new member? → *A Maintainer (or group Owner).*
3. Which role is the normal working role? → *Developer.*

---

[⬅️ 05 · Create or join a project](05-create-or-join-a-project.md) · [07 · How FINTEC organizes projects ➡️](07-how-fintec-organizes-projects.md)
