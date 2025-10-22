# DevOps Academy – Day 3: Remotes, Tags, Releases, Stashes & Undo (Student Pack)

Welcome to **Day 3** of the DevOps Academy!  Today you’ll build on your branching and merging skills by collaborating on a real **GitHub** repository.  You’ll discover how to configure and manage remotes, synchronise changes with `fetch`, `pull` and `push`, mark important points in history with annotated and lightweight tags, publish releases through the GitHub web interface, temporarily shelve work using the stash, and safely undo mistakes using reset and revert.  By the end of the day you will have pushed your demo project to GitHub, created a release from a tag and practised stashing and undo operations while collaborating asynchronously.  Use this guide to follow along with the instructor‑led session and to support your self‑paced labs.

## Schedule & Activities

You are expected to be on site from **09:30 to 17:00**.  Only the **09:30–11:00** block is instructor‑led; the remainder of the day is devoted to labs, reflection and peer feedback.  Plan your time using the table below:

| Time | Mode | Activity |
|---|---|---|
| **09:30–11:00** | Instructor‑Led | Live lecture and demos covering remotes and remote‑tracking branches, fetch/pull/push commands, managing remotes, tagging and releasing, stashing and cleaning, undoing history with `reset` vs `revert`, and exploring the commit graph.  A formative Kahoot concludes this block. |
| **11:00–12:30** | Self‑study | **Lab A:** create a personal GitHub repository, push your demo project, practise synchronising with `fetch`, `pull` and `push`, create annotated and lightweight tags, push tags to GitHub and draft a release.  Submit your self‑check by 12:30. |
| **12:30–13:30** | Break | Lunch. |
| **13:30–15:30** | Self‑study | **Lab B:** experiment with stashing and cleaning (use options like `--keep-index` and `-u` for untracked files).  Practise undoing history with `reset` and `revert`, push your changes to GitHub and, if desired, create a new tag and release to mark a stable state.  Submit your self‑check by 15:30. |
| **15:30–17:00** | Peer Review | Exchange release links or commit references with classmates, fetch and merge each other’s work from GitHub, discuss resets vs reverts, and complete a final Kahoot.  Instructors are available for questions. |

## Learning Objectives

By the end of Day 3 you should be able to:

* List configured remotes, view their URLs and understand the purpose of remote‑tracking branches.
* Distinguish between `git fetch`, `git pull` and `git push`, and know when to use each.
* Create and list lightweight and annotated tags, view tag details, push tags to a remote and understand how GitHub releases build on tags.
* Use `git stash` to save work in progress, list stashes and apply or drop them with appropriate options.
* Undo changes safely with `git reset` and `git revert`, recognising when each is appropriate.
* Publish a release on GitHub from a tag, including a title, release notes and optional attachments, and understand the difference between a tag and a release.

## Key Concepts & Terminology

### Remote repositories & tracking branches

A **remote repository** is a copy of your project stored in another location (for example, on a different machine or directory).  Remotes allow you to share code with collaborators.  The command `git remote` lists the remotes configured for your repository; `git remote -v` shows the fetch and push URLs.  When you communicate with a remote, Git updates your **remote‑tracking branches** (like `origin/main`) to reflect the state of branches on the remote.  Remote‑tracking branches are read‑only pointers that update when you run `git fetch` or `git pull`.

### Synchronising: fetch vs pull vs push

* **Fetch** (`git fetch`) downloads new commits from the remote and updates your remote‑tracking branches.  It does **not** change your current branch or working directory.
* **Pull** (`git pull`) is a convenience command that performs a fetch followed by an automatic merge.  Use it when you’re ready to integrate upstream changes into your current branch.
* **Push** (`git push`) uploads your local commits to the remote.  If someone else has pushed new commits since you last fetched, your push may be rejected; fetch and merge first.

### Managing remotes

You can add, rename, inspect and remove remotes:

* `git remote add <name> <url>` – Add a new remote by specifying a short name and its URL or filesystem path.
* `git remote rename <old> <new>` – Rename an existing remote; Git updates your configuration and tracking branches automatically.
* `git remote show <name>` – Display detailed information about the remote, including fetch/push URLs and which local branches track remote branches.
* `git remote remove <name>` – Remove a remote and delete its remote‑tracking branches.  Use this with caution.

### Tagging & releases

**Tags** mark specific commits, often to indicate releases or milestones.  Two types of tags exist:

* **Lightweight tag** – A simple pointer to a commit, like a branch name that doesn’t move.  Create one with `git tag <tagname>`.
* **Annotated tag** – A full object stored in the database containing the tagger’s name, email, date and a message.  Create one with `git tag -a <tagname> -m "message"`.  View tag details with `git show <tagname>`.

List all tags with `git tag`.  Push tags to a remote using `git push <remote> --tags`.

On **GitHub**, releases are built on top of tags.  A release packages your project at the tagged commit and lets you add a title, release notes and optional binary attachments.  You create a release from the GitHub web interface by selecting an existing tag, filling in the release details and publishing it.  Release dates may differ from the tag dates.

### Stashing & cleaning

`git stash` saves the current state of your working directory and index on a stack, then reverts your working tree to a clean state.  Use `git stash list` to see saved entries and `git stash show` to preview changes.  Apply saved work with `git stash apply` (leaving the entry in the stash) or `git stash pop` (apply and remove).  Options include:

* `--keep-index` – Stash only unstaged changes; staged changes remain staged.
* `-u` / `--include-untracked` – Include untracked files in the stash.

### Undoing history: reset vs revert

* **Reset** (`git reset`) moves the current branch pointer to another commit.  It can modify the index and working directory depending on the mode:
  * `--soft` – Move the pointer only; leave index and working directory unchanged.
  * `--mixed` (default) – Move the pointer and update the index; leave working directory unchanged.
  * `--hard` – Move the pointer and reset both index and working directory to match the target commit.
    Because reset rewrites history, only use it on local commits that haven’t been shared.
* **Revert** (`git revert <commit>`) creates a new commit that undoes the changes introduced by the specified commit.  Revert preserves the existing history and is safe to use on shared branches.

### Remote collaboration & commit graph

In this course you will collaborate through **GitHub** rather than using a local simulation.  After pushing your changes to the remote, use `git log --graph --oneline --all` to explore branch divergence and convergence.  Collaborators will clone your GitHub repository, fetch and merge your changes from the remote and, if needed, open pull requests through the GitHub interface.

## Essential Commands

| Command | Purpose |
|--------|---------|
| `git remote` / `git remote -v` | List configured remotes and view their fetch/push URLs. |
| `git fetch` | Download new commits and update remote‑tracking branches without merging. |
| `git pull` | Fetch and automatically merge into your current branch. |
| `git push` | Upload your local commits to the remote. |
| `git remote add <name> <url>` | Add a new remote. |
| `git remote rename <old> <new>` | Rename an existing remote. |
| `git remote show <name>` | Show detailed information about a remote. |
| `git remote remove <name>` | Remove a remote and its tracking branches. |
| `git tag -a <tagname> -m "message"` | Create an annotated tag. |
| `git tag <tagname>` | Create a lightweight tag. |
| `git tag` | List tags. |
| `git show <tagname>` | View the details of a tag. |
| `git push <remote> --tags` | Push your tags to a remote. |
| `git stash` | Save your working directory and index on a stack and revert to a clean state. |
| `git stash list` | List stashed entries. |
| `git stash apply` / `git stash pop` | Reapply stashed changes (pop removes them). |
| `git reset --soft|--mixed|--hard <target>` | Move the current branch pointer and optionally update the index and working directory. |
| `git revert <commit>` | Create a new commit that undoes the specified commit. |

## Lab A – Remote Setup, Synchronising & Tagging (11:00–12:30)
### Goal

Create a personal GitHub repository, synchronise your local project with `fetch`, `pull` and `push`, and create tags and releases.

### Steps

1. **Prepare your project** – Extract `git_demo_repo_day3.zip`.  Initialise the repository if necessary (`git init`), stage and commit all files (`git add .` and `git commit -m "Initial commit"`), and configure your user name and email: `git config user.name "Your Name"` and `git config user.email "you@example.com"`.
2. **Create a GitHub repository and push** – On GitHub, create a new repository (for example, `git-demo-day3`).  Add it as a remote in your local repo (`git remote add origin https://github.com/<your‑username>/git-demo-day3.git`) and push your commits to GitHub (`git push -u origin main`).
3. **Synchronise and collaborate** – If working with a partner, ask them to clone the same GitHub repository and create a new branch; otherwise, create a new branch yourself (e.g. `feature/update-notes`), make a change, commit and push it.  Then, on your `main` branch, run `git fetch` and `git merge origin/<branch>` to integrate the remote changes.
4. **Create and push tags** – Create an annotated tag (`git tag -a v1.0 -m "First release"`) and a lightweight tag (`git tag v1.0-lw`).  List tags with `git tag` and push them to GitHub (`git push origin --tags`).  Confirm on GitHub that the tags appear.
5. **Draft a release** – In the GitHub web interface, click **Releases** and **Draft a new release**.  Select your annotated tag (`v1.0`), enter a title and release notes, optionally upload a file from the project, and publish the release.
6. **Self‑check and submit** – Answer the questions below in your notebook or digital copy and submit them to the instructor by **12:30**.

### Self‑Check for Lab A

1. What is the difference between `git fetch` and `git pull`?
2. How do tags and releases differ on GitHub?
3. Which commands do you use to create and push an annotated tag?
4. How do you draft a release from a tag on GitHub?
5. Why might you create a lightweight tag in addition to an annotated one?

## Lab B – Stashing & Undoing History (13:30–15:30)
### Goal

Learn how to use the stash to save work in progress, explore different stash options, and practise undoing changes with reset and revert.  You will push your changes to GitHub and use tags and releases to mark stable points after undo operations.

### Steps

1. **Make changes and stash** – open `notes.txt` and add a few lines.  Stage some of the changes with `git add` but leave others unstaged.  Run `git stash push -m "WIP: notes edits"` to save your work and return to a clean working tree.  Use `git stash list` to verify that your stash was created.
2. **Switch clones and create commits** – Ask a colleague to create a new branch `topic/cleanup` and make a change to `notes.txt` and then commit and push the branch. fetch and merge these changes into your `main` branch.
3. **Apply and drop the stash** – Apply your stash with `git stash apply`.  Resolve any conflicts that arise (edit the file to keep the correct changes, then `git add` and `git commit`).  Drop the stash entry with `git stash drop` or use `git stash pop` if you prefer to apply and remove in one step.
4. **Experiment with options** – Create a new change and stash only the unstaged part using `git stash --keep-index`.  Create another change and stash untracked files using `git stash -u`.  Apply these stashes and note the differences.
5. **Undo history** – Make two new commits on `main`.  Use `git reset HEAD~1` (default mixed) to move the branch pointer back one commit while preserving your working directory changes.  Inspect the status and log.  Then make another commit and use `git revert HEAD` to create a new commit that undoes it.  Compare the history after each operation.
6. **Create a new tag & release** – After performing your undo operations, create another annotated tag (for example, `v1.1`) and push it to GitHub.  Use the GitHub web interface to draft a new release from this tag, summarising the changes you made and providing context for your classmates.
7. **Self‑check and submit** – Answer the questions below and submit them by **15:30**.

### Self‑Check for Lab B

1. What does `git stash` do to your working directory and index?  How can you view the stashes you have saved?
2. When would you use `git stash apply` versus `git stash pop`?
3. What is the effect of using `--keep-index` and `-u` when stashing?
4. How does `git reset` differ from `git revert`?  When is each appropriate?
5. How do tags and releases help you mark stable points after undoing history?  Describe the steps to create a new release from a tag on GitHub.

## Peer Review Guidelines

During the peer review session (15:30–17:00), exchange change summaries with classmates and practise reviewing each other’s work.  Use this checklist:

* **Pull before review** – Always fetch and merge the latest changes from the remote before starting your review.
* **Read the summary** – Read the change summary carefully.  Does it explain why the changes were made?
* **Check commit quality** – Are commits logically grouped and messages descriptive?  Are tags used appropriately?
* **Review stash usage** – Have stashes been applied and dropped correctly?  Are there any lingering stash entries that should be cleaned up?
* **Discuss resets and reverts** – If a reset was performed, was it done safely on a private branch?  Was revert used appropriately on shared history?

## Additional Resources

Looking to deepen your understanding?  Consult these resources after class:

* *Pro Git* by Chacon & Straub – Chapters on “Working with Remotes,” “Remote Branches,” “Tagging,” and “Stashing and Cleaning”.
* The Git documentation on [`git request-pull`](https://git-scm.com/docs/git-request-pull) – Learn how to generate change summaries for code review.
* The Atlassian tutorial “Git Reset vs Git Revert” – Explains the difference between these commands and when to use each.

Happy coding and have fun exploring the wider world of Git!