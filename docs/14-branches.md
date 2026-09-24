# 14 · Branches — what they are and how to create one

> ⏱️ **~10 min** · 🎯 **Level: Beginner** · 🧰 **Tool needed: Web, Web IDE, or terminal — all three shown**

---

## Why branches exist (30-second story)

Two FINTEC developers edit the same project **directly** on `main`:

- Siti is halfway through a new interest-calculation feature. The code doesn't run yet.
- Raj, meanwhile, needs to fix an urgent typo customers see **right now**.
- …but Raj can't push his fix, because `main` is full of Siti's half-finished work. 🙃

**A branch breaks this deadlock.** A branch is a separate line of work copied from `main`:

```
main:  ──●───────────●───────●──►   always kept working
               │            ▲
               ▼            │ merge (via Merge Request)
  12-show-total-interest    │
        └──●──●──●──────────┘   Siti's messy playground — private until done
```

- Siti works on her branch — messy, safe, invisible to everyone
- Raj fixes the typo on `main` immediately
- When Siti finishes, her branch merges back in one clean step

**Rule of thumb: one task = one branch.** No shared branch, no "work directly on main" — ever.

> 📌 The default branch is called **`main`**. It's protected by default: Developers can't push to it directly ([06 · Roles](06-roles-and-permissions.md)). That protection is *why* branches aren't optional at FINTEC.

## Naming your branch

Convention (recommended, in line with [24 · Linking issues](24-link-issues-branches-merge-requests.md)):

```text
<issue-number>-<short-description>

12-show-total-interest      ✅
17-fix-safari-nan-bug       ✅
my-stuff-final2             ❌
```

Lowercase, dashes, no spaces. The issue number prefix is the magic that links work to its task — [24](24-link-issues-branches-merge-requests.md) explains.

## Create a branch — three ways

### Way 1 · Terminal (the developer habit)

```bash
# 0. start from the latest code (always!)
git switch main
git pull

# 1. create + switch to your new branch
git switch -c 12-show-total-interest

# 2. confirm you're on it
git branch        # → * 12-show-total-interest, main
```

> 📖 Old tutorials say `git checkout -b 12-show-total-interest` — same thing, older command. `switch` is the modern, less confusing one.

### Way 2 · GitLab website (no terminal)

1. Project page → left sidebar **Code → Branches**
2. Click **New branch**
3. **Branch name:** `12-show-total-interest`
4. *(Create from:* `main` — the default, leave it)
5. **Create branch** → done; it appears in the branch list

### Way 3 · From an Issue (the FINTEC shortcut ✨)

On the Issue page (e.g. Issue #12), click **Create merge request** — GitLab creates a *correctly named branch* **and** starts the linked Merge Request in one click. The full story: [24 · Linking Issues, Branches and Merge Requests](24-link-issues-branches-merge-requests.md).

### Way 4 · Inside the Web IDE

Open the Web IDE ([09](09-create-and-upload-files.md)) → click the **branch name** in the bottom-left status bar → **Create new branch** → type the name → confirm.

## The one rule that prevents 80% of pain

> ⚠️ **Always create your branch from an up-to-date `main`.**
> Terminal: `git switch main` → `git pull` → `git switch -c <name>`. Skipping the `pull` means your branch starts from yesterday's code — and merge time becomes conflict time ([22 · Fix merge conflicts](22-fix-merge-conflicts.md)).

## What "being on a branch" means

Your files on disk instantly change to that branch's version when you switch. Uncommitted edits follow you (or block you — see [28 · Common mistakes](28-common-mistakes-and-recovery.md) if Git refuses to switch). Check where you are with `git status` — it says `On branch …` in the first line.

## Deleting a branch afterwards

After its Merge Request merges, GitLab offers a **Delete source branch** checkbox — tick it, it's good hygiene ([21 · Approve and merge](21-approve-and-merge.md)). Locally: `git branch -d 12-show-total-interest`.

## ✅ Check yourself

1. Why work on a branch instead of `main`? → *Keeps `main` working; your half-done changes stay private until reviewed.*
2. Where should a new branch come from? → *An up-to-date `main`.*
3. Best branch name for task #17, a NaN bug on Safari? → *`17-fix-safari-nan-bug`.*

---

[⬅️ 13 · Everyday Git commands](13-everyday-git-commands.md) · [15 · Making changes ➡️](15-making-changes.md)
