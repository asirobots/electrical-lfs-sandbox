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

## Step 0 — you should already have this cloned

If you followed the pre-meeting instructions, you're done here. Get into the
repo and make sure you have today's version of these instructions:

```bash
cd /c/GitLocal/electrical-lfs-sandbox
git pull
```

---

## Step 1 — where am I?

```bash
git status
```

Read the output. It tells you what branch you're on and whether you have
uncommitted changes. **You will run this command more than any other.** When
something feels wrong, run it first — it's written for humans, and it usually
names the command you want next.

You should see `On branch master` and `nothing to commit, working tree clean`.

---

## Step 2 — make your branch and switch to it

Today everyone uses the same shape: `training/lastname-firstname`

```bash
git checkout -b training/lastname-firstname
```

So Jane Smith types:

```bash
git checkout -b training/smith-jane
```

`-b` means "create it". `checkout` switches you onto it. Git confirms with
`Switched to a new branch`.

**All lowercase, hyphens between words. You should never need the Shift key
to type a branch name** — not the letters, not the hyphen, not the slash.
If you pressed Shift, you typed it wrong.

> **What just happened:** you made yourself a private workspace. Nothing you
> do from here affects anyone else until you push it and open a Pull Request.

---

## Step 3 — do your "work": sign the guestbook

On a real day this is where you'd do your actual engineering. Today, create
a text file in the `guestbook` folder named after yourself.

Jane Smith creates `guestbook/JaneSmith.txt`:

```bash
touch guestbook/JaneSmith.txt
notepad guestbook/JaneSmith.txt
```

`touch` makes an empty file; `notepad` opens it. Put in just your name and
your market:

```
Jane Smith
dozer
```

Save it and close Notepad.

> **Note on the name:** the no-Shift-key rule is for **branch names**.
> Filenames just need to be sensible — capitals are fine here.

---

## Step 4 — what did Git notice?

```bash
git status
```

Your file appears under **Untracked files**. Git can see it, but it isn't
watching it yet — Git doesn't assume everything in the folder belongs in
the repo.

**Read the line Git prints underneath.** It tells you exactly what to do
next: *use "git add &lt;file&gt;..." to include in what will be committed.*

---

## Step 5 — do what Git just told you

```bash
git add guestbook/JaneSmith.txt
```

---

## Step 6 — check again

```bash
git status
```

Now it's under **Changes to be committed**. You've told Git "this is part of
my next save."

> **Why is this two steps?** With one file it feels like busywork. On a real
> change you might touch six files and only want three of them in this
> commit. `add` is you choosing what goes in; `commit` is you saving that
> choice.

---

## Step 7 — commit

```bash
git commit -m "Add Jane Smith to guestbook"
```

> **You must include `-m` and a message in quotes.** Leave it off and Git
> opens a full-screen editor called vim, which is genuinely hard to escape.
> If that happens: press **Esc**, type **:q!**, press Enter. Then run the
> command again with `-m`.

---

## Step 8 — check again

```bash
git status
```

Clean working tree, and **"Your branch is ahead of 'origin/...' by 1 commit"**.
You've saved it locally. Nobody else can see it yet.

---

## Step 9 — push

```bash
git push -u origin training/smith-jane
```

Now it exists on GitHub. `-u` links your local branch to the one on the
server, so next time plain `git push` is enough.

Look at the output — GitHub prints you a link for opening a Pull Request.

---

## Step 10 — check one more time

```bash
git status
```

**"Your branch is up to date with 'origin/...'"** — local and server now
match.

---

## Step 11 — open the Pull Request (in your browser)

Click the link Git printed, or go to the repo on GitHub and use the
**Compare & pull request** button.

- Base: `master`
- Compare: your branch
- Leave the title as-is and click **Create pull request**

Notice the title GitHub wrote for you — it came from your branch name, for
free. That's what a good branch name buys you.

Then watch the screen share. We'll merge them live.

---

## Done early?

1. **See the history.** `git log --oneline --graph --all` — every commit,
   every branch, in one picture.
2. **See what you actually committed.** `git show` prints your last commit
   in full.
3. **Look at everyone else's.** Once a few PRs are merged, `git checkout master`,
   `git pull`, and look in the `guestbook` folder. Every file in there
   arrived exactly the way yours did.
4. **Help your neighbor.** Seriously — this is the most useful option.

---

## If something goes wrong

Run `git status` and read it out loud. Nine times out of ten it names the
command you need.

If you're stuck, paste the **exact** error into the meeting chat. Don't
paraphrase it, and don't start trying fixes you found on Google — half the
answers out there are for situations that aren't yours.

**Nothing you can do in this repo is unrecoverable.** That's the point of
having a sandbox.
