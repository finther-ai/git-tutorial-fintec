# 04 · Groups → Projects → Repositories

> ⏱️ **~7 min** · 🎯 **Level: Absolute beginner** · 🧰 **Tool needed: a web browser**

---

## The mental model

GitLab organizes everything in two levels, like folders on a computer:

```
🏢 GROUP  (a team or department — a container)
│
├── 📁 PROJECT  (one product / app / repo)
│      └── 🗄️ REPOSITORY  (the project's files + full history)
│
├── 📁 PROJECT
└── 📁 PROJECT
```

| Level | Plain English | FINTEC example |
|---|---|---|
| **Group** | A shared workspace for a team. Holds members, projects, and settings that apply to all of them | `ai-fintec` — the FINTEC AI group |
| **Project** | One product or piece of work. In GitLab, "project" and "repository" go together — creating a project automatically creates its repository | `loan-calculator`, `git-tutorial-fintec` |
| **Repository** | The project's **file storage and history**. When people say "clone the repo", they mean *download a full copy of the project's files and history* | The files inside `ai-fintec/loan-calculator` |

> 📌 **In everyday speech** you'll hear these words used loosely: *"push it to the repo"*, *"add me to the project"*, *"check the ai-fintec group"*. Now you know exactly what each means.

## Why the group matters

The **group** (`ai-fintec`) is where team-level things happen:

- 👥 **Membership** — you're added to the group once and inherit access to the group's projects (with a role — see [06 · Roles and permissions](06-roles-and-permissions.md))
- 🧭 **A stable home** — every project gets an address like `gitlab.com/ai-fintec/<project-name>`
- 🏷️ **Shared labels and settings** — consistent issue labels and rules across projects

> 💡 **Groups can contain subgroups** (e.g. `ai-fintec / products / loan-calculator`). Useful for bigger organizations — an *optional* recommendation for FINTEC structure is covered in [07 · How FINTEC organizes projects](07-how-fintec-organizes-projects.md).

## The address of everything

GitLab URLs follow the structure exactly:

```
https://gitlab.com/<group>/<project>

https://gitlab.com/ai-fintec/loan-calculator
└─────┬─────┘└────┬────┘└──────┬───────┘
   gitlab.com  the group   the project
```

Inside a project, add the section you want:

| You want to see… | URL ends with… |
|---|---|
| The files | `/-/blob/main/<file>` |
| All branches | `/-/branches` |
| Issues | `/-/issues` |
| Merge requests | `/-/merge_requests` |

## Your personal space

You also have a personal namespace (`gitlab.com/<your-username>/…`) — anything you create outside a group lives there. **At FINTEC, real project work belongs in the `ai-fintec` group, not personal namespaces** — that's where teammates can find it, and where it survives when someone is on leave or leaves the company.

## ✅ Check yourself

1. What comes directly under a group? → *Projects.*
2. What does a repository contain? → *The project's files and their full history.*
3. A teammate says "clone the repo" — what do they want? → *A full copy of the project's files and history on your computer* ([11 · Clone a project](11-clone-a-project.md)).

---

[⬅️ 03 · Sign in and explore the interface](03-sign-in-and-the-interface.md) · [05 · Create or join a project ➡️](05-create-or-join-a-project.md)
