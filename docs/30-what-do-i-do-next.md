# 30 · "What do I do next?" — the everyday answer page

> ⏱️ **~5 min** · 🎯 **Level: Everyone** · 🧰 **Tool needed: none (this is the map)**

---

## The page to keep open

Bookmark this one. It answers the only question that matters in daily work: **"I want to do X — what do I click or do next?"**

## 🧭 The big three answers

Most days are one of these:

| Your situation | Your next move |
|---|---|
| 🆕 **Completely new here** | [01 · What is GitLab?](01-what-is-gitlab.md) → follow the numbers, top to bottom |
| 🎫 **I have a task to do** | [26 · The FINTEC workflow](26-the-fintec-workflow.md) — the loop, step by step |
| 🆘 **Something went wrong** | [28 · Common mistakes and recovery](28-common-mistakes-and-recovery.md) — symptom → fix |

## "I want to…" — the full index

### Getting set up

| I want to… | Go |
|---|---|
| Understand what GitLab even is | [01](01-what-is-gitlab.md) |
| Create my account | [02](02-create-your-gitlab-account.md) |
| Find my way around the interface | [03](03-sign-in-and-the-interface.md) |
| Understand groups/projects/repos | [04](04-groups-projects-and-repositories.md) |
| Join a project / get access | [05](05-create-or-join-a-project.md) |
| Know what my role allows | [06](06-roles-and-permissions.md) |
| Understand how FINTEC organizes work | [07](07-how-fintec-organizes-projects.md) |

### Doing the work

| I want to… | Go |
|---|---|
| Create a new project | [08](08-create-a-project-from-scratch.md) |
| Add/upload/edit files — no installs | [09](09-create-and-upload-files.md) |
| Decide: web, Web IDE, terminal, glab? | [10](10-choosing-your-tool.md) |
| Get a project onto my computer | [11](11-clone-a-project.md) |
| Understand Git without the jargon | [12](12-git-concepts-in-plain-english.md) |
| See the essential commands | [13](13-everyday-git-commands.md) |
| Start my task properly | [14 · Branches](14-branches.md) + [23 · Issues](23-issues.md) |
| Make & commit changes | [15](15-making-changes.md) + [16](16-commits.md) |
| Share / update my work | [17 · Push](17-push.md) + [18 · Pull](18-pull.md) |

### Working with the team

| I want to… | Go |
|---|---|
| Ask for my code to be merged | [19 · Create a Merge Request](19-create-a-merge-request.md) |
| Review a teammate's MR | [20](20-review-a-merge-request.md) |
| Merge approved work | [21](21-approve-and-merge.md) |
| Fix a merge conflict | [22](22-fix-merge-conflicts.md) |
| Report a bug / request a feature | [23 · Issues](23-issues.md) |
| Link issue → branch → MR | [24](24-link-issues-branches-merge-requests.md) |
| Write a decent README | [25](25-readme-and-documentation.md) |
| See the whole workflow at once | [26](26-the-fintec-workflow.md) |
| Watch it happen, start to finish | [27 · Project walkthrough](27-project-walkthrough.md) |

### When things go sideways

| I want to… | Go |
|---|---|
| Undo something — anything | [28 · Common mistakes and recovery](28-common-mistakes-and-recovery.md) |
| Handle a password/token/secret scare | [29 · Security basics](29-security-basics.md) · **act first: rotate, then report** |
| Use SSH, `glab`, stash, protected-branch settings | [Advanced](advanced/01-ssh-access.md) — optional, later |

## Rapid troubleshooting table

| Symptom | Likely cause → jump |
|---|---|
| Git asks for a password | It wants your **access token**, not your password → [10](10-choosing-your-tool.md) |
| `404` on a project | Private + not a member → [05](05-create-or-join-a-project.md) |
| Can't push to `main` | Protection working as intended → branch + MR → [14](14-branches.md) |
| Push rejected, "fetch first" | Teammate pushed first → `git pull` → [17](17-push.md)/[18](18-pull.md) |
| `CONFLICT` during pull/merge | Normal → calm walkthrough → [22](22-fix-merge-conflicts.md) |
| Merge button greyed out | Read the reason next to it → [21](21-approve-and-merge.md) |
| Merged but issue still open | Missing `Closes #n` → [24](24-link-issues-branches-merge-requests.md) |
| "My local copy is behind" | `git pull` → [18](18-pull.md) |
| Committed a secret 🚨 | **Rotate now**, then → [29](29-security-basics.md) |
| "I broke everything" | You didn't → [28](28-common-mistakes-and-recovery.md) |

## Still stuck? The escalation ladder

1. **Re-read the symptom's guide above** — 80% of blocks are answered there
2. **Ask your team / team lead** — in the open (project channel or an Issue comment), not a DM: the answer helps the next person too
3. **Check GitLab's status & official docs** — [status.gitlab.com](https://status.gitlab.com) if the site itself misbehaves · [docs.gitlab.com](https://docs.gitlab.com) for everything deep
4. **Email the tutorial team: [finther.ai@finther.my](mailto:finther.ai@finther.my)** — for guide feedback, access questions nobody can answer, or anything this ladder doesn't cover

> 💡 When you ask, include: *what you tried, the exact error text, and a screenshot*. A question with those three things usually gets answered in one round-trip.

## And after guide 30?

There's no exam. 🎉 The real graduation is running the loop on your first real task:

```text
Issue → Branch → Work → Commit → Push → Merge Request → Review → Merge
```

…with [26 · The FINTEC workflow](26-the-fintec-workflow.md) open in a tab. By the second or third run you won't need the tab — and the optional [Advanced guides](advanced/01-ssh-access.md) will still be there when you're curious.

**Welcome to FINTEC. Go merge something. 🚀**

---

[⬅️ 29 · Security basics](29-security-basics.md) · [🏠 Back to the guide map](../README.md)
