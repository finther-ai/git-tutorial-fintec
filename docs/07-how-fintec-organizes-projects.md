# 07 · How FINTEC organizes projects

> ⏱️ **~7 min** · 🎯 **Level: Beginner** · 🧰 **Tool needed: none (reading + recommendations)**

---

## What this guide is

A **recommended way of keeping the `ai-fintec` group tidy** as more employees and projects arrive.

> ⚠️ **Important honesty note:** unless your team lead says otherwise, **this is a recommendation, not an official FINTEC policy.** The defaults below follow common GitLab practice. If FINTEC publishes official rules, those win.

## The recommended shape

```
gitlab.com/ai-fintec
│
├── 📁 git-tutorial-fintec      ← the guide you're reading (onboarding)
├── 📁 <product-1>              ← one repo per product / app
│     ├── frontend?             ← split only when it genuinely helps
│     └── ...
├── 📁 <internal-tool-1>        ← tools built for FINTEC itself
├── 📁 <data-analysis-1>        ← analyses, reports, notebooks
└── 📁 <docs-or-standards>      ← company-wide docs, templates
```

## Recommendation 1 · One project = one purpose

A project holds **one product, one tool, or one piece of work** — not "everything team X does".

| ❌ Avoid | ✅ Prefer |
|---|---|
| `fintec-everything` (300 unrelated files) | `loan-calculator`, `expense-dashboard`, `einvoice-parser` |
| `old-stuff-v2-FINAL-real` | one project, cleaned up; delete dead experiments |
| Personal sandbox projects in the group | personal experiments in your own namespace, or clearly named `sandbox-<your-name>` |

**Why:** small, focused projects are easier to find, easier to give access to, and easier to hand over when someone leaves.

## Recommendation 2 · Predictable naming

Use lowercase words separated by dashes: `loan-calculator`, `client-onboarding-api`.

- The name should make sense to a new employee on day one
- Dashes, not spaces or underscores — URLs and terminals behave better
- No versions in names (`-v2`, `-final`, `-new`) — GitLab already keeps history ([01 · What is GitLab?](01-what-is-gitlab.md))

## Recommendation 3 · Subgroups when you outgrow a flat list

GitLab groups can nest:

```
ai-fintec
├── products
│   ├── loan-calculator
│   └── expense-dashboard
├── internal
│   ├── hr-portal
│   └── git-tutorial-fintec
└── data
    └── market-reports
```

**When:** roughly past ~10–15 projects, or when different sub-teams need different members.
**Until then:** a flat group is simpler. Don't organize for imaginary scale.

## Recommendation 4 · Every project carries a README

The rule of thumb: *a stranger should understand the project from its GitLab front page in 60 seconds.* What to put there: [25 · READMEs and documentation](25-readme-and-documentation.md).

## Recommendation 5 · Work lives in Issues and Merge Requests, not chats

Task discussed in a chat app and nowhere else = lost history. Open an **Issue** ([23](23-issues.md)), link it to the **Merge Request** ([24](24-link-issues-branches-merge-requests.md)), and the decision trail becomes part of the project forever.

## If you're setting a project up right now

This is the last "thinking" guide — everything after is hands-on:

👉 **[08 · Create a project from scratch](08-create-a-project-from-scratch.md)** walks you through every click.

## ✅ Check yourself

1. One project should contain…? → *One product / tool / piece of work.*
2. Are these rules official FINTEC policy? → *Only if your team lead says so — otherwise they're sensible defaults.*
3. Where does an experiment belong? → *Your personal namespace or a clearly-named sandbox project — not the main group.*

---

[⬅️ 06 · Roles and permissions](06-roles-and-permissions.md) · [08 · Create a project from scratch ➡️](08-create-a-project-from-scratch.md)
