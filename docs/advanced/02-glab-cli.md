# Advanced · 02 · `glab` — GitLab from the terminal

> ⏱️ **~10 min** · 🎯 **Level: Optional — power users** · 🧰 **Tool needed: terminal + Git**

---

## What `glab` is

**GitLab's official command-line tool.** Where `git` moves code, `glab` talks to *GitLab itself* — Issues, Merge Requests, releases — from the terminal, without opening the browser.

> 🎯 **Perspective check:** everything `glab` does, the website does too ([10 · Choosing your tool](../10-choosing-your-tool.md)). Learn it when the browser round-trip genuinely slows you down — usually a few months in. Zero shame in the browser.

## Install & authenticate

Install (pick your OS — full list: [gitlab.com/gitlab-org/cli](https://gitlab.com/gitlab-org/cli)):

```bash
# macOS
brew install glab

# Windows (winget or scoop)
winget install GLab.GLab
scoop install glab

# Linux (Debian/Ubuntu — see the repo for other distros)
# …follow the official install docs for your distro
```

Authenticate once:

```bash
glab auth login
```

Answer the prompts: **GitLab.com** → HTTPS → yes, authenticate → it opens your browser to authorize (or accepts a Personal Access Token with `api` scope — [10 · tokens](../10-choosing-your-tool.md)). Done — `glab` now knows who you are, per project.

## The everyday commands

Run inside a cloned project (it detects `origin` automatically):

| Command | What it does |
|---|---|
| `glab mr list` | All open Merge Requests — the review queue at a glance |
| `glab mr create --fill` | Open an MR: fills title/description from your commit, prompts to confirm |
| `glab mr view 13` | Read MR !13 (add `--web` to jump to the browser) |
| `glab mr checkout 13` | Fetch a teammate's MR branch locally to run/test it |
| `glab mr merge 13` | Merge (when it's yours to merge — [21 · Approve and merge](../21-approve-and-merge.md)) |
| `glab issue list` / `glab issue create` | Browse and file Issues without the browser |
| `glab repo view --web` | Open the current project's GitLab page |

### The classic flow, glab-flavoured

```bash
git switch -c 12-show-total-interest      # branch — still plain git ([14](../14-branches.md))
# …work, commit ([15](../15-making-changes.md)–[16](../16-commits.md))…
git push -u origin 12-show-total-interest # push ([17](../17-push.md))
glab mr create --fill --draft             # MR in one line, as a draft ([19](../19-create-a-merge-request.md))
# …review happens in the browser or…:
glab mr view 13                           # check comments
glab mr merge 13 --remove-source-branch   # merge + tidy ([21](../21-approve-and-merge.md))
```

## Where `glab` genuinely shines

- **Reviewing from your machine:** `glab mr checkout 13` → run the code *before* approving ([20 · Reviewing](../20-review-a-merge-request.md)) — the strongest form of review there is
- **Bulk/triage moments:** `glab issue list --label bug` beats clicking through five pages
- **Scripting:** opening ten similar MRs, automating release chores — if you type it twice, consider scripting it
- **SSH-free convenience:** pairs with HTTPS auth; one `glab auth login` covers it

## Rules of the road

- `glab` **doesn't replace `git`** — branching, committing, pushing stay `git` ([13 · Everyday Git commands](../13-everyday-git-commands.md)); `glab` is the GitLab-services layer on top
- **Merging still follows the FINTEC loop** — approvals and review are social contracts, not buttons; `glab mr merge` doesn't exempt you from [21](../21-approve-and-merge.md)
- Everything is still visible in the web UI — teammates without `glab` see the same Issues/MRs you made

## 🚫 Troubleshooting

| Symptom | Fix |
|---|---|
| `glab: command not found` | Install step missed, or PATH — reopen the terminal first |
| `401/403` errors | `glab auth login` again — token expired or too few scopes |
| Works in one repo, not another | Run `glab auth login`'s project setup, or you're outside a Git clone |
| Confused about what it did | Every command has `--help`, and the web UI shows the same result |

---

[⬅️ Advanced · 01 · SSH access](01-ssh-access.md) · [Advanced · 03 · Protected branches & approvals ➡️](03-protected-branches-and-approvals.md)
