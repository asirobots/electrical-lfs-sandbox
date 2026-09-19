# Exercise: sign the guestbook

**Goal:** get one file of your own into this repo, on a properly named
branch, through a Pull Request. That's it. That's the whole skill.

Everything below happens in **Git Bash**, inside your clone of this repo.

Take your time. If you fall behind, say so in the meeting chat — the point
is that everybody finishes, not that anybody finishes fast.

---

## Step 0 — where am I?

```bash
git status
```

Read the output. It tells you what branch you're on and whether you have
uncommitted changes. You will run this command more than any other. When
something feels wrong, run it first.

You should see `On branch main` and `nothing to commit, working tree clean`.

---

## Step 1 — start from the latest main

```bash
git checkout main
git pull
```

`checkout` switches branches. `pull` downloads whatever other people have
merged since you last looked. **Always start a new branch from an up-to-date
`main`** — it saves you conflicts later.

---

## Step 2 — make your branch

```bash
git checkout -b <your-market>/guestbook-<your-name>
```

For example:

```bash
git checkout -b dozer/guestbook-jsmith
```

The `-b` means "create it". All lowercase, hyphens between words.

Check it worked:

```bash
git status
```

It should now say `On branch dozer/guestbook-jsmith`.

> **What just happened:** you made a private workspace. Nothing you do on this
> branch affects anyone else until you push it and open a PR.

---

## Step 3 — add your file

Create a file at `guestbook/<your-name>.md`. Use any editor — Notepad is fine.

Put whatever you like in it. A suggestion:

```markdown
# Jane Smith

- Market: dozer
- Years doing EE work: 12
- One thing I want Git to stop doing to me:
```

Save it.

---

## Step 4 — look at what Git noticed

```bash
git status
```

Your new file shows up under **Untracked files**. Git can see it, but it
isn't watching it yet.

---

## Step 5 — stage it

```bash
git add guestbook/<your-name>.md
git status
```

Now it shows under **Changes to be committed**. You've told Git "this is part
of my next save."

> **Why two steps?** `add` lets you choose *which* changes go into a commit.
> On a real change you might touch six files and only want three of them in
> this commit.

---

## Step 6 — commit

```bash
git commit -m "Add Jane Smith to guestbook"
```

That's a save point in your local history. It still only exists on your
machine.

---

## Step 7 — push

```bash
git push -u origin <your-market>/guestbook-<your-name>
```

Now it exists on GitHub. The `-u` links your local branch to the remote one,
so next time plain `git push` is enough.

Look at the output — GitHub prints a link for opening a Pull Request.

---

## Step 8 — open the Pull Request

Click that link, or go to the repo on GitHub and use the **Compare & pull
request** button.

- Base: `main`
- Compare: your branch
- Give it a title, click **Create pull request**

Then watch the screen share. We'll merge them live.

---

## Done early?

Try one of these:

1. **See the history.** `git log --oneline --graph --all` — every commit,
   every branch, in one picture.
2. **See what you actually committed.** `git show` prints your last commit
   in full. `git log -p guestbook/` shows the history of just that folder.
3. **Cause a merge conflict on purpose.** Add a line with your name to
   `guestbook/ATTENDEES.md` on your branch, commit, and push. If someone
   else edited a nearby line, you'll get a conflict when we merge. This is a
   *good* thing to see happen while somebody is standing next to you.
4. **Help your neighbor.** Seriously — this is the most useful option.

---

## If something goes wrong

Run `git status` and read it out loud. Nine times out of ten it names the
command you need.

If you're stuck, paste the **exact** error into the meeting chat. Don't
paraphrase it and don't start trying fixes you found on Google — half the
answers out there are for situations that aren't yours.

**Nothing you can do in this repo is unrecoverable.** That's the point of
having a sandbox.
