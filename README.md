# Git Demo Repository

Welcome to the **Git Demo Repository** for the DevOps Academy course.  This project is intentionally simple and designed solely to give you a controlled environment to practise basic Git commands on Linux or using Git Bash.

## Purpose

You will use this repository to:

- Initialise a local Git repository and then **create a remote on GitHub** to collaborate.  Follow the course instructions to push your local history to the remote and manage branches there.
- Add, modify and delete files to see how Git tracks changes.
- Create branches and experiment with merging or rebasing.
- Practise writing clear commit messages and performing rollbacks.

## Structure

```
git_demo_repo/
├── README.md        # This file: overview and instructions
├── docs/            # Markdown notes you can edit and track
│   ├── history.md   # A short essay about the history of DevOps
│   └── glossary.md  # Glossary of key terms to be updated during the lab
├── notes.txt        # Plain‑text scratchpad for quick edits
├── scripts/         # Simple shell scripts to practise modifications
│   ├── hello.sh     # Prints a greeting; modify it to personalise the output
│   └── deploy.sh    # Placeholder deployment script for later labs
└── .gitignore       # Ignore unwanted files (e.g., editor backups)
```

Feel free to create additional files or folders during the exercises, but keep them organised.

## Getting Started

1. Clone or copy this folder into your Linux VM or Git Bash environment.
2. Open a terminal in the `git_demo_repo` directory.
3. Run `git init` to initialise the repository.
4. Sign in to your GitHub account and create a new empty repository.  Add the GitHub repository as a remote with `git remote add origin <URL>`.
5. Use the provided lab instructions to stage, commit, branch and merge changes, then push to your GitHub remote when instructed.

If you are unfamiliar with any of the commands, consult the cheat sheet provided in the course materials or the official [Git documentation](https://git-scm.com/docs).