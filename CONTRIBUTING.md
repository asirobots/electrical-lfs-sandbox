# How we use this repo

This is the **sandbox**. Break things here on purpose. Nothing here ships.
The conventions below are the same ones we use in `electrical-lfs`, so the
habits you build here are the habits you want.

---

## The one rule

> **Your work lives on a branch with a proper name, and reaches `main` through release-candidate Pull Request then a main Pull Request.**

Your work does not live on `main`. Not on somebody else's branch. Not on a shared catch-all branch where nobody can tell whose work is whose.

---

## Branch naming

```
<market>/<topic>
```

All lowercase. Hyphens between words. For example:

```
ag/pump-ctrl-rev-b
dozer/harness-rework
compactor/vibe-motor-swap
<your-market>/sensor-cal-update
```

Markets that want more structure may add a subtopic:

```
adt-wt/pump-ctrl/sensor-cal
adt-wt/pump-ctrl/wiring
```

### The rules, and why

| Rule | Why |
|---|---|
| All lowercase | Git branch names are case-sensitive on GitHub but **not** on Windows. Mixed casing lets two branches exist on the server that your PC can't tell apart. Tab-completion is also case-sensitive, so lowercase means less hand-typing. |
| Hyphens, not underscores or spaces | One convention, consistently. `pump-ctrl` and `pump_ctrl` are two different branches. |
| **A name is a branch OR a folder of branches, never both** | Git stores each branch as a real file on disk. If `adt-wt/pump-ctrl` exists as a branch, then `adt-wt/pump-ctrl/sensor-cal` can't be created — you can't have a file and a folder with the same name. **If you think you'll want sub-branches under a topic, don't create the bare topic branch.** |
| Never start with a hyphen | Git reads a leading `-` as a command-line flag and the errors are baffling. |
| `release-candidate` is reserved | See below. Don't use it as an ordinary topic name. |

---

## How work reaches `main`

```
   your branch              market collection point         everyone
                                                               |
 ag/pump-ctrl-rev-b  --PR-->  ag/release-candidate  --PR-->  main
 ag/harness-rework   --PR-->      (market review)          (final review)
```

1. You branch off `main` or your market's `release-candidate` and do your work.
2. You open a PR into **`<market>/release-candidate`**. Your market reviews it.
3. When the market is ready, `<market>/release-candidate` is PR'd into `main`.
   That one triggers the platform level review.

Nobody commits directly to `main`. Not even the repo admin — the server refuses it.

> **Note:** this sandbox calls its default branch `main`. The real repo,
> `electrical-lfs`, calls it `master`. Same idea, different name — `main` is
> GitHub's newer default and `master` is the older one. You'll see both in the
> wild, so it's worth knowing they mean the same thing.

---

## After your PR merges

Delete the feature branches. GitHub offers a **Delete branch** button right on the
merged PR; use it.

To stop seeing deleted branches as ghosts in `git branch -a`, run this once
on each machine you use:

```bash
git config --global fetch.prune true
```

Deleting a branch on GitHub does **not** un-delete itself when a teammate
pushes. A plain `git push` only pushes the branch you're currently on.

---

## Files

**In this sandbox:** plain text files only. Nothing special to do.

**In the real repo (`electrical-lfs`):** Danfoss GUIDE files (`.p1x`, `.p1d`,
`.scs`) are tracked by **Git LFS**, and `.lhx` build output is ignored and never
committed. Day to day this changes nothing about how you work — you still `add`,
`commit` and `push` exactly the same way. That's the point of LFS: it stays out
of your way.

The one thing worth knowing now: **a file only goes into LFS if the rule existed
before its first commit.** Adding a rule later doesn't fix a file that's already
in history. So if you're about to commit a file type nobody has committed before,
ask first.

---

## If you're stuck

`git status` almost always tells you what's going on. Read it before doing
anything else — it's written for humans and it usually names the command
you want next.

When that isn't enough, stop and ask rather than guessing. Nothing in this
sandbox is precious, but the habit of asking early is worth building.
