# 22 · Fix merge conflicts (calmly)

> ⏱️ **~12 min** · 🎯 **Level: Beginner (with a deep breath)** · 🧰 **Tool needed: Web IDE (easiest) or terminal**

---

## First: a conflict is not an error

A **merge conflict** just means: *two branches changed the same lines, and Git politely refuses to guess which version wins.* It stops and asks a human — you. **Nothing is broken, nothing is lost.** Every developer alive has resolved hundreds of these.

## How conflicts happen (30-second story)

- You and Raj both branch from `main` ([14 · Branches](14-branches.md))
- You change line 20 of `calculator.js` on `12-show-total-interest`
- Raj changes **line 20 of the same file** on his branch — and merges first
- You try to merge yours → Git: *"you both edited line 20 — you decide."*

```
main:                ──●──●──●──●──●   (Raj's line-20 change is in here)
                            ▲
12-show-total-interest:     │
             └──●──●──✖️────┘   your line-20 change meets Raj's → conflict
```

Conflicts become *likely* when branches live long — one more reason to keep branches small and merge quickly ([15 · golden rule](15-making-changes.md)).

## Where you'll meet one

| Moment | Symptom |
|---|---|
| Merging an MR ([21](21-approve-and-merge.md)) | Widget: **"This merge request contains merge conflicts"**, Merge blocked |
| `git pull` / `git merge` ([18](18-pull.md)) | `CONFLICT (content): Merge conflict in calculator.js` |

Same situation, two doors. Pick your fix below.

## Fix a conflict — Way 1 · GitLab's built-in resolver (easiest)

On the blocked MR page:

1. Click **Resolve conflicts** (button in the merge widget)
2. GitLab shows each conflicting file; conflicts appear as **two editable boxes** ( *"ours"* vs *"theirs"* )
3. Choose per conflict: **Use ours** / **Use theirs**, or edit the text into the correct combined version
4. **Commit resolutions** → GitLab creates a merge-commit on your branch; the MR becomes mergeable again ✅

Works only for straightforward conflicts — for anything tangled, use Way 2.

## Fix a conflict — Way 2 · Web IDE (visual, no terminal)

On the MR page: click **Resolve in Web IDE** (or open the branch in the Web IDE from [09](09-create-and-upload-files.md)). The IDE's **Merge conflict editor** shows both versions side by side — click the lines you want to keep (mix and match freely), then commit.

## Fix a conflict — Way 3 · terminal (full control)

```bash
# 0. bring your branch up to date first — clean start
git switch 12-show-total-interest
git pull

# 1. try the merge
git merge main

# 2. Git refuses and reports the conflicting files
#    CONFLICT (content): Merge conflict in calculator.js

# 3. open calculator.js — find the conflict markers:
```

```js
<<<<<<< HEAD
const total = amount * years * 0.045;      // your version
=======
const total = amount * (1 + 0.045) ** years; // main's version (Raj's)
>>>>>>> main
```

4. **Read the three parts:** between `<<<<<<< HEAD` and `=======` is *your* branch; between `=======` and `>>>>>>> main` is *the incoming* version. Edit the block so it contains the **correct final code** — often one, sometimes a true combination of both — and **delete all three marker lines**

```js
const total = amount * (1 + 0.045) ** years;   // ✅ resolved, markers gone
```

5. Repeat per conflict. Check for stragglers:

```bash
git status                 # "both modified" files still need work
git diff                   # markers gone everywhere? (search: <<<<<<< )
```

6. **Commit the resolution:**

```bash
git add calculator.js
git commit                 # Git pre-fills a "Merge branch 'main'…" message — keep it
git push
```

The MR updates itself and becomes mergeable ([21 · Approve and merge](21-approve-and-merge.md)). Done. 🎉

## How to choose the right version

Ask, in order:

1. Which version is **factually correct**? (test it!)
2. Do both changes matter? → combine them deliberately
3. Genuinely ambiguous? → ask the other author (Raj is one chat away) or the reviewer. **That's not weakness — that's teamwork.**

> ⚠️ **The one real danger of conflict resolution:** clicking through and keeping the wrong version. Markers make *both* versions look plausible. Always re-read the resolved block as final code, and if the project runs tests — run them before pushing.

## Abort button (yes, there's an undo)

Getting lost mid-resolution? Step out cleanly:

```bash
git merge --abort        # terminal: back to exactly where you were
```

The Web IDE and GitLab resolver simply let you cancel — nothing is committed until you say so. Breathe, maybe grab the tutorial project to practise on, come back.

## Preventing most conflicts

- **Small branches, merged quickly** ([15](15-making-changes.md)) — the biggest lever
- **`git switch main && git pull` before branching** ([14](14-branches.md))
- **Merge `main` into your long-lived branch every day or two** ([18 · Pull](18-pull.md))
- **Talk** — if you and Raj are touching the same file, a 2-minute sync saves a 20-minute conflict

## ✅ Check yourself

1. What does a conflict actually mean? → *Same lines changed on two branches; Git needs a human decision.*
2. Easiest fix for a simple MR conflict? → *MR page → Resolve conflicts → pick/edit → Commit resolutions.*
3. What must never survive in committed code? → *The `<<<<<<<` / `=======` / `>>>>>>>` markers.*

---

[⬅️ 21 · Approve and merge](21-approve-and-merge.md) · [23 · Issues ➡️](23-issues.md)
