# 05 · Create or join a project

> ⏱️ **~7 min** · 🎯 **Level: Beginner** · 🧰 **Tool needed: a web browser**

---

## Two situations, one guide

You either **join** a project that already exists (most common for new employees) or **create** a brand-new one. This guide covers joining; creating from scratch gets its own deep-dive in [08 · Create a project from scratch](08-create-a-project-from-scratch.md).

## Situation A · Join an existing project

### Step 1 · Find out who owns it

Your team lead or project Manager adds people to projects. Ask them: *"Please add me to `<project name>`"* and mention **the GitLab username you created** in [02](02-create-your-gitlab-account.md) (e.g. `siti.rahman`).

### Step 2 · Watch for the notification

Once added, GitLab usually notifies you by email. You'll now see the project on your dashboard:

1. Sign in → avatar (top-right) → **Your work**? — simpler: click **Projects** in the left sidebar, or
2. Just search: top bar → **Search** → type the project name → Enter.

### Step 3 · Confirm what you can do

Open the project and check the left sidebar:

- See **Plan → Issues** and **Code → Repository**? ✅ You have access.
- Something's missing or everything says *404*? ❌ You're not (fully) added yet — go back to your team lead and tell them which role you need (see [06 · Roles and permissions](06-roles-and-permissions.md) so you use the right word).

> 💡 **Pro move:** bookmark the projects you use daily (Ctrl/Cmd + D on the project page).

## Situation B · "Why can't I see the project at all?"

FINTEC projects are typically **private** — they don't exist for you until you're a member. A `404` page on GitLab usually means *"you don't have access"*, not *"this doesn't exist"*. Ask the project owner to add you.

> 📌 **Visibility levels** (set by whoever owns the project):
> | Level | Who can see it |
> |---|---|
> | **Private** | Members only — the FINTEC default for real work |
> | **Internal** | Any signed-in GitLab user |
> | **Public** | Anyone on the internet |

## Situation C · Create a new project (quick version)

Need to start something new? Short version — full walkthrough in the next-but-three guide:

1. Top bar → **➕ (New…)** → **New project/repository**
2. Choose **Create blank project** (or import if migrating)
3. Give it a name and put it **in the `ai-fintec` group** — not your personal namespace
4. Tick **Initialize repository with a README** ✅
5. Click **Create project**

👉 Full details, naming rules, and options: **[08 · Create a project from scratch](08-create-a-project-from-scratch.md)**

> 💡 **Recommended (general practice, not an official FINTEC policy):** before creating a new project, search whether one already exists — duplicates rot. And if your work is a small experiment, ask your lead whether it belongs in the group at all.

## Who adds people? (roles preview)

Adding members requires the **Maintainer** role (or Owner at group level). So in practice: *you ask someone senior, they click two buttons.* The full role table is next:

👉 **[06 · Roles and permissions](06-roles-and-permissions.md)**

## ✅ Done when…

- [x] You can open your team's project from your dashboard or search
- [x] You know to ask your team lead (with your username) when you're missing access

---

[⬅️ 04 · Groups, projects & repositories](04-groups-projects-and-repositories.md) · [06 · Roles and permissions ➡️](06-roles-and-permissions.md)
