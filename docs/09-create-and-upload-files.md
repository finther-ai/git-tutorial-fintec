# 09 · Create and upload files (no installation needed)

> ⏱️ **~10 min** · 🎯 **Level: Beginner** · 🧰 **Tool needed: a web browser**

---

## The good news first

**You can create, edit, and upload files entirely in the browser.** For documentation, configs, and small fixes, this is often the *right* choice — not just the easy one. No Git installation, no terminal, nothing.

> 📌 Terminology: files live in the **repository** — the project's file storage and history ([01 · What is GitLab?](01-what-is-gitlab.md)). Any change you make here is tracked and reversible. Nothing is ever "just overwritten into oblivion".

## A · Create a new file in the web editor

### Step by step

1. Open the project page
2. Click **Edit ▾** (next to the blue `Code` button) → **New file**
   *(or navigate into a folder and use **+** → this file)*
3. **Name the file** in the header field
   - `meeting-notes.md`, `config.yaml`, `runbook.md`
   - Include the extension: `.md` for Markdown, `.txt`, `.yaml`, …
   - Create a folder *while* naming: type `docs/guide.md` → folder `docs/` appears ✨
4. Type or paste the content in the editor
5. Check the **Preview** tab (Markdown files render nicely)
6. Click **Commit changes** — a panel slides in:

   | Field | What to do |
   |---|---|
   | **Commit message** | A one-line summary: `Add meeting notes for 24 Sep` ([16 · Commits](16-commits.md) teaches good messages) |
   | **Target Branch** | ⚠️ Default is a **new branch** like `siti.rahman-patch-1` — keep that! It leads you straight into a Merge Request. Only commit **directly to `main`** if it's your own doc project and you're sure ([14 · Branches](14-branches.md) explains why) |
7. Click **Commit changes** again to confirm

> 💡 If you committed to a new branch, GitLab offers **Create merge request** right away — that's exactly the FINTEC flow ([19 · Create a Merge Request](19-create-a-merge-request.md)).

## B · Edit an existing file

1. Open the file in the repository view
2. Click the **✏️ pencil icon** (top-right of the file) → it opens in the same editor
3. Edit → **Commit changes** → same panel as above

> 💡 **Perfect for:** typos, wording fixes, updating a date, small config changes. This is the fastest legal way to fix a README.

## C · Upload files from your computer

1. Project page → **Edit ▾** → **Upload file**
2. Drag & drop or browse — pick one or several files
3. Optional: change the **target folder** (prefix the path, e.g. `docs/`)
4. Write a commit message → **Commit changes**

> ⚠️ **Upload limits & good manners:** individual files are capped (roughly the size of a large PDF — exact limits vary by instance). **Don't use GitLab to store ZIPs of data dumps, videos, or database backups** — repositories are for *text-first project files*. Big binary artifacts belong in proper storage. Ask your lead where those live.

## D · The Web IDE — when the web editor isn't enough

For editing **multiple files at once**, or anything bigger than a quick fix:

**Edit ▾ → Open in Web IDE** → a full code editor in your browser tab: file tree on the left, tabs, search across files, and a *Preview* for Markdown. Same commit panel when you're done — with a clear list of *every* changed file.

| Situation | Use |
|---|---|
| One small file | Web editor (A/B) |
| Several files, one logical change | **Web IDE** |
| Real development work, ongoing | Terminal + Git ([11 · Clone a project](11-clone-a-project.md)) |

## Markdown in 60 seconds

Most files you create at first will be `.md` (**Markdown**) — plain text with simple symbols for formatting. Cheat sheet:

```markdown
# Big heading          ## Smaller heading
**bold**               *italic*
- bullet point         1. numbered item
[link text](https…)    ![image](path)
`inline code`
```

Preview tab → see it rendered before committing. More in [25 · READMEs and documentation](25-readme-and-documentation.md).

## ✅ Practice now (5 minutes, safely)

In this tutorial's project — or a sandbox project in your personal namespace:

1. Create `notes/hello.md` with one heading and one sentence about yourself
2. Commit it **to a new branch**, keeping the default branch name
3. Open the Merge Request GitLab offers

You've just done, in miniature, the exact loop you'll repeat every day. 🎉

---

[⬅️ 08 · Create a project from scratch](08-create-a-project-from-scratch.md) · [10 · Choosing your tool ➡️](10-choosing-your-tool.md)
