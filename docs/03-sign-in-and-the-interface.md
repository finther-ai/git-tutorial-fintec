# 03 · Sign in and understand the GitLab interface

> ⏱️ **~10 min** · 🎯 **Level: Absolute beginner** · 🧰 **Tool needed: a web browser**

---

## What you'll learn

Where things live in GitLab, so the rest of the guides never leave you lost. GitLab's menus get occasional redesigns — **don't memorize pixels, memorize what things are called.** This guide teaches you the vocabulary.

## 1. Sign in

1. Go to **[https://gitlab.com](https://gitlab.com)** → **Sign in**
2. Enter your email/username + password (and your 2FA code, if you enabled it)

You land on your **dashboard**. If anything looks empty — that's normal. You haven't joined any projects yet.

## 2. The four areas you need to know

```
┌────────────────────────────────────────────────────────────┐
│ ① TOP BAR            Search · + (new) · avatar (profile)   │
├──────────────┬─────────────────────────────────────────────┤
│ ② LEFT       │                                             │
│   SIDEBAR    │        ③ MAIN CONTENT AREA                  │
│   (menu)     │        (files, issues, merge requests…)     │
│              │                                             │
│              │        ④ RIGHT SIDE (contextual)            │
│              │        activity, related MRs, details       │
└──────────────┴─────────────────────────────────────────────┘
```

### ① The top bar

- 🔍 **Search** — type a project or issue name and jump straight to it. Genuinely the fastest way around.
- **➕ (New…)** — create a new project, group, or snippet.
- **👤 Your avatar** — your profile, preferences, and sign out.

### ② The left sidebar (changes with context!)

This is the main navigation. **Its contents change depending on where you are:**

- On your **personal dashboard** it shows *your* things: Your work, Projects, Groups…
- Inside a **project** it switches to that project's menu: Plan, Manage, Code, Build, Analyze…

> 📌 The most common beginner confusion: *"The menu disappeared/changed!"* — You just navigated into (or out of) a project. Use **Your work → Projects** or the **search bar** to get your bearings. If the sidebar is hidden, a **left-pointing chevron icon** at the far left edge expands it.

### ③ The main content area

Whatever you clicked: a file, a list of issues, a Merge Request discussion. This is where you actually work.

### ④ Project landing page (the one page to learn well)

Open any project and you'll see:

| Element | What it is |
|---|---|
| **File list** | The files and folders of the project (the repository) |
| **README preview** | The project's front-page documentation, rendered below the file list ([25 · READMEs and documentation](25-readme-and-documentation.md)) |
| **`Code` ▾ button** | Where the **clone link** lives — how you copy the project to your computer ([11 · Clone a project](11-clone-a-project.md)) |
| **`Edit` ▾ button** | Edit files — including the **Web IDE** ([10 · Choosing your tool](10-choosing-your-tool.md)) |
| **Branch dropdown** (`main ▾`) | Which version of the files you're looking at ([14 · Branches](14-branches.md)) |
| **Issues / Merge request counters** | Quick links to the project's tasks ([23](23-issues.md)) and proposed changes ([19](19-create-a-merge-request.md)) |

## 3. Your safety net: the search bar

Lost? Top bar → click **Search** → type the project name (e.g. `loan-calculator`) → press Enter. You're there. This works for issues, Merge Requests, and people too.

## 4. Take the 5-minute tour (do this now)

1. Go to the FINTEC group: **[https://gitlab.com/ai-fintec](https://gitlab.com/ai-fintec)** *(you may not see much until you're added — that's expected for private groups)*
2. Open this very tutorial project: **[https://gitlab.com/ai-fintec/git-tutorial-fintec](https://gitlab.com/ai-fintec/git-tutorial-fintec)**
3. Click through the left sidebar: **Plan → Issues**, **Code → Repository**, **Code → Merge requests** — just look around. You can't break anything by reading. 🙂
4. Click your avatar → **Edit profile** — see where your name, email, and settings live.

## ✅ Check yourself

1. The left sidebar changed — what does it mean? → *You moved between personal pages and inside a project.*
2. Where is the clone link? → *Project page → `Code` ▾ button.*
3. Fastest way to find a project? → *The search bar in the top bar.*

---

[⬅️ 02 · Create your GitLab account](02-create-your-gitlab-account.md) · [04 · Groups, projects & repositories ➡️](04-groups-projects-and-repositories.md)
