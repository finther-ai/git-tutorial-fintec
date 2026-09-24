# 25 · READMEs and project documentation

> ⏱️ **~8 min** · 🎯 **Level: Beginner** · 🧰 **Tool needed: web browser or Web IDE**

---

## Why the README is the most-read file you'll write

The **README** is the file GitLab shows on a project's front page — it's the project's shop window, its manual, and its onboarding doc in one. The 60-second test:

> *A new teammate opens the project cold. Sixty seconds later, do they know what it is, how to run it, and whom to ask?*

If yes — the README works. And remember: **the reader is a teammate who just joined, or you in six months.** Same person, effectively. 🙂

## What goes in a README

A solid beginner template — steal it:

```markdown
# Loan Calculator

Estimates monthly loan repayments and total interest for FINTEC customers.
Related: issues with label `loan-calc` · #issue-number for the current milestone.

## What it does
- Monthly payment + total interest from amount / term / rate
- Handles empty and invalid input gracefully

## How to run it
1. Install Node.js 20+
2. `npm install && npm start`
3. Open http://localhost:3000

## How to contribute
1. Pick or open an Issue → 23 · Issues
2. Branch from `main`: `<issue-number>-<short-name>` → 14 · Branches
3. Open a Merge Request that says `Closes #<n>` → 19 · Merge Requests

## Who to ask
- Owner: @ahmad.lee · Questions: #loan-calc team channel
```

Keep it **short**. A README nobody finishes is a README nobody reads. Link out to deeper docs instead of pasting them in.

## README mechanics (creating and editing it)

- **Creating:** project without one? Click **"Create README"**? — or just: **Edit ▾ → New file**, name it exactly `README.md` (uppercase name, `.md` extension) → [09 · Create and upload files](09-create-and-upload-files.md)
- **Editing:** open the file → **✏️ pencil icon** → edit → Preview tab → commit to a branch → MR. For a small wording fix on your own project, editing directly is fine; for team projects, treat README changes like any change ([14 · Branches](14-branches.md))
- **It renders automatically:** the project front page shows the rendered version below the file list. Preview before committing — headers, links and tables are easy to fumble

## Markdown, just enough

| You type | You get |
|---|---|
| `# Title` · `## Section` · `### Sub` | headings (one `#` per page, please) |
| `**bold**` · `*italic*` · `` `code` `` | **bold** · *italic* · `code` |
| `- item` | bullet list |
| `1. item` | numbered list |
| `[text](https://…)` · `[file](docs/guide.md)` | web link · **link to a file in the repo** |
| `![alt](img/logo.png)` | image (commit it into the repo, e.g. an `img/` folder) |
| ``` ``` fenced blocks ``` ``` | code / command blocks — *always* for commands |
| `> quote` | blockquote, nice for callouts |

> 💡 A table of contents isn't needed on GitLab — the front page renders one automatically in the right panel. One less thing to maintain.

## Documentation that lives *next to* code

Beyond the README, common (optional, per-project) files:

| File | Purpose |
|---|---|
| `README.md` | the front page — always |
| `docs/` folder | longer guides, runbooks, meeting notes — [09 · files](09-create-and-upload-files.md) shows folder creation |
| `CHANGELOG.md` | notable changes per release — only if the team maintains it |
| `.gitignore` | tells Git which files to *never* track (`node_modules/`, `.env`) → **[29 · Security basics](29-security-basics.md)** |
| `CONTRIBUTING.md` | house rules, if your project has unusual ones |

> 📌 **GitLab wikis** (left sidebar **Plan → Wiki**) exist for free-standing docs. Recommendation: start with `docs/` files in the repo — they version, review, and travel *with* the code. Reach for the wiki only when the team agrees.

## Documentation habits that age well

- **Fix docs in the same MR as the change that invalidated them.** "Docs update" PRs never happen; "oops, same MR" ones always do ([15 · golden rule](15-making-changes.md))
- **Prefer examples over prose.** A copy-pasteable command beats three paragraphs describing it
- **Delete aggressively.** Docs describing the old way are worse than no docs
- **Review docs like code.** A `Nit:` in a README comment is a legitimate review finding ([20 · Reviewing](20-review-a-merge-request.md))

## 🚫 Common problems

| Problem | Fix |
|---|---|
| README shows as raw text, not rendered | File must be `README.md` (with extension) and contain valid Markdown — check headings have spaces after `#` |
| Links to repo files are broken | Use **relative** links (`docs/setup.md`, `../README.md`) — they work on GitLab and in clones. Full URLs break the moment anything moves |
| Front page still says "Getting started" template | Replace it — that's GitLab's auto-text; a placeholder README undermines the project's credibility |
| README conflicts with reality | Same rule as any code: fix the file, open an Issue if you can't fix it now ([23 · Issues](23-issues.md)) |

## ✅ Check yourself

1. The 60-second test? → *New teammate: what is it, how to run, whom to ask — in one minute.*
2. Right way to link to `docs/setup.md` from the README? → *Relative link: `docs/setup.md`.*
3. Code changes the README's instructions — when do docs update? → *In the same MR.*

---

[⬅️ 24 · Linking Issues, Branches and Merge Requests](24-link-issues-branches-merge-requests.md) · [26 · The FINTEC workflow ➡️](26-the-fintec-workflow.md)
