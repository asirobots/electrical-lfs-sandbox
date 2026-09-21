# Exercise: sign the guestbook

**Goal:** get one file of your own into this repo, on a properly named
branch, through a Pull Request. That's it. That's the whole skill.

Everything below happens in **Git Bash**, inside your clone of this repo.

Take your time. If you fall behind, say so in the meeting chat — the point
is that everybody finishes, not that anybody finishes fast.

> ### Before you start: this repo is public
>
> Anyone on the internet can read it. Put nothing in your file that you
> wouldn't put on a public website — no customer names, no project details,
> no phone numbers, no part numbers. Your name and your market, that's it.
>
> Getting in the habit of asking *"should this be public?"* before you commit
> is worth more than anything else in this exercise.

---

## Step 0 — where am I?

```bash
git status
```

Read the output. It tells you what branch you're on and whether you have
uncommitted changes. You will run this command more than any other. When
something feels wrong, run it first.

You should see `On branch master` and `nothing to commit, working tree clean`.

---

## Step 1 — start from the latest master

```bash
git checkout master
git pull
```

`checkout` switches branches. `pull` downloads whatever other people have
merged since you last looked. **Always start a new branch from an up-to-date
`master`** — it saves you conflicts later.

---

## Step 2 — make your branch

Today everyone uses the same shape: `training/lastname-firstname`

```bash
git checkout -b training/lastname-firstname
```

So Jane Smith types:

```bash
git checkout -b training/smith-jane
```

The `-b` means "create it".

**All lowercase, hyphens between words. You should never need the Shift key
to type a branch name** — not for the letters, not for the hyphen, not for
the slash. If you pressed Shift, you typed it wrong.

Check it worked:

```bash
git status
```

It should now say `On branch training/smith-jane`.

> **What just happened:** you made yourself a private workspace. Nothing you
> do on this branch affects anyone else until you push it and open a PR.

---

## Step 3 — add your file

Name it the same way as your branch. Jane Smith creates
`guestbook/smith-jane.md`:

```bash
touch guestbook/smith-jane.md
notepad guestbook/smith-jane.md
```

`touch` makes an empty file; `notepad` opens it. Put in just this:

```markdown
# Jane Smith

- Market: dozer
```

Save it and close Notepad.

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
git add guestbook/smith-jane.md
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

> **You must include the `-m` and a message in quotes.** If you leave it off,
> Git opens a full-screen editor called vim and it is genuinely hard to get
> back out of. If that happens to you: press **Esc**, then type **:q!** and
> press Enter. Then run the command again with `-m`.

That's a save point in your local history. It still only exists on your
machine.

---

## Step 7 — push

```bash
git push -u origin training/smith-jane
```

Now it exists on GitHub. The `-u` links your local branch to the remote one,
so next time plain `git push` is enough.

Look at the output — GitHub prints a link for opening a Pull Request.

---

## Step 8 — open the Pull Request

Click that link, or go to the repo on GitHub and use the **Compare & pull
request** button.

- Base: `master`
- Compare: your branch
- Leave the title as-is and click **Create pull request**

Notice the title GitHub wrote for you — it came from your branch name, for
free. That's what a good branch name buys you.

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
