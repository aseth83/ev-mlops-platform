# Git Made Easy — Beginner Cheat Sheet

## 1. What is Git?

Git is a tool that keeps track of changes in your project.

Think of it like this:

```text
Your project files
      ↓
Git watches changes
      ↓
You choose what to save
      ↓
Git creates a checkpoint
```

That checkpoint is called a **commit**.

---

# 2. Git vs GitHub

## Git

Git runs on your computer.

It helps you:

- track file changes
- create commits
- create branches
- switch between versions
- compare changes

## GitHub

GitHub is an online place where your Git repository can be stored.

```text
Your computer
     │
     │ git push
     ▼
GitHub
```

And in the other direction:

```text
GitHub
     │
     │ git pull
     ▼
Your computer
```

---

# 3. What is a Git repository?

A Git repository is a normal project folder that also contains Git information.

Example:

```text
C:\AI-ML-Projects\ev-mlops-platform
│
├── .git
├── README.md
├── src
└── tests
```

The hidden `.git` folder tells Git:

> This folder is a Git repository.

Git stores information about commits, branches, remotes, history and configuration inside `.git`.

---

# 4. How does Git know which project you are working on?

Git looks at your current folder.

You can check your PowerShell folder with:

```powershell
Get-Location
```

You can check the root of the Git repository with:

```powershell
git rev-parse --show-toplevel
```

---

# 5. Cloning a GitHub repository

Go to the parent folder:

```powershell
cd "C:\AI-ML-Projects"
```

Then run:

```powershell
git clone https://github.com/YOUR-USERNAME/ev-mlops-platform.git
```

Git automatically creates:

```text
C:\AI-ML-Projects\ev-mlops-platform
```

Then move into it:

```powershell
cd ev-mlops-platform
```

---

# 6. The most important Git workflow

Remember this:

```text
Edit
 ↓
Add
 ↓
Commit
 ↓
Push
```

Or:

```text
Working folder
     ↓ git add
Staging area
     ↓ git commit
Local Git history
     ↓ git push
GitHub
```

---

# 7. `git status`

Command:

```powershell
git status
```

Use it often.

It tells you:

- which branch you are on
- which files changed
- which files are untracked
- which files are staged
- whether there is anything to commit

Example:

```text
On branch main

Untracked files:
    README.md
```

Meaning:

> README.md exists, but Git is not tracking it yet.

---

# 8. `git add`

Example:

```powershell
git add README.md
```

Meaning:

> Put README.md into the staging area for the next commit.

To stage all changed files:

```powershell
git add .
```

Be careful with `git add .` because it stages all current changes.

---

# 9. What is the staging area?

The staging area is a preparation area for the next commit.

Think of it like packing a box:

```text
Working files
     ↓
git add
     ↓
Files selected for the box
     ↓
git commit
     ↓
Box is sealed as a checkpoint
```

---

# 10. `git commit`

Example:

```powershell
git commit -m "docs: add initial project README"
```

Meaning:

> Create a checkpoint from the files currently staged.

Important:

```text
-m
```

means:

```text
message
```

It does **not** mean filename.

So this:

```powershell
git commit -m README.md
```

would create a commit whose message is simply `README.md`.

A better commit is:

```powershell
git commit -m "docs: add initial project README"
```

---

# 11. Good commit messages

Examples:

```text
docs: add initial project README
feat: add prediction endpoint
test: add data validation tests
fix: handle missing SOC values
refactor: simplify training pipeline
```

Common prefixes:

| Prefix | Meaning |
|---|---|
| `docs:` | Documentation |
| `feat:` | New feature |
| `fix:` | Bug fix |
| `test:` | Tests |
| `refactor:` | Code restructuring |
| `chore:` | Maintenance/setup |

---

# 12. What is a branch?

A branch is a separate line of work.

Example:

```text
main
 │
 ├── feature/api
 ├── feature/data-validation
 └── fix/model-loading
```

Usually `main` is the primary branch.

---

# 13. How does Git know which branch you are on?

Git uses something called `HEAD`.

Think of HEAD as:

> Which branch am I currently working on?

Example:

```text
HEAD
 ↓
main
```

Check your current branch:

```powershell
git branch --show-current
```

Or:

```powershell
git branch
```

Example:

```text
* main
```

The `*` means this is your current branch.

---

# 14. `git branch -M main`

Command:

```powershell
git branch -M main
```

Meaning:

> Rename the current branch to `main`.

This command does not choose the project folder.

Git already knows the repository from your current folder and the `.git` directory.

---

# 15. What is `origin`?

When you clone a GitHub repository, Git normally gives the remote GitHub repository the name:

```text
origin
```

Check it with:

```powershell
git remote -v
```

Example:

```text
origin  https://github.com/YOUR-USERNAME/ev-mlops-platform.git (fetch)
origin  https://github.com/YOUR-USERNAME/ev-mlops-platform.git (push)
```

Think of `origin` as a nickname for your GitHub repository.

---

# 16. Local branch vs GitHub branch

```text
main
```

is your local branch.

```text
origin/main
```

represents the remote `main` branch on GitHub.

Conceptually:

```text
Your computer              GitHub

main  ------------------>  main
          git push

main  <------------------  main
          git pull
```

---

# 17. `git push`

Example:

```powershell
git push -u origin main
```

Meaning:

> Send my local `main` branch commits to the GitHub repository called `origin`.

`-u` remembers this connection for future pushes.

After the first push, you can normally use:

```powershell
git push
```

---

# 18. `git pull`

Command:

```powershell
git pull
```

Meaning:

> Get newer changes from GitHub and bring them into my current local branch.

---

# 19. `git fetch`

Command:

```powershell
git fetch
```

Meaning:

> Check/download information about remote changes without automatically merging them into my current branch.

Beginner shortcut:

```text
git fetch = check what changed remotely
git pull  = fetch + bring changes into your branch
```

---

# 20. Simple example from start to finish

Suppose you create `README.md`.

Check:

```powershell
git status
```

Stage it:

```powershell
git add README.md
```

Create a commit:

```powershell
git commit -m "docs: add initial project README"
```

Push it:

```powershell
git push -u origin main
```

---

# 21. Useful commands for our AI/ML course

## Where am I?

```powershell
Get-Location
```

## Which Git repository am I inside?

```powershell
git rev-parse --show-toplevel
```

## What is happening in this repository?

```powershell
git status
```

## Which branch am I on?

```powershell
git branch --show-current
```

## Show all local branches

```powershell
git branch
```

## Which GitHub repository is connected?

```powershell
git remote -v
```

## Stage one file

```powershell
git add README.md
```

## Stage all current changes

```powershell
git add .
```

## Create a commit

```powershell
git commit -m "message describing the change"
```

## Push commits to GitHub

```powershell
git push
```

## Get latest changes

```powershell
git pull
```

## Show commit history

```powershell
git log --oneline
```

---

# 22. Beginner safety check

Before important Git work, run:

```powershell
Get-Location
git branch --show-current
git status
git remote -v
```

This tells you:

```text
Where am I?
Which branch am I on?
What changed?
Which GitHub repository is connected?
```

---

# 23. Mental model to remember

```text
PROJECT FOLDER
      │
      ├── files
      │
      └── .git
            │
            ↓
      LOCAL GIT REPOSITORY
            │
            ├── commits
            ├── branches
            └── remote = origin
                       │
                       ▼
                    GITHUB
```

---

# 24. The four commands you will use most

```powershell
git status
git add .
git commit -m "describe your change"
git push
```

Think:

```text
Check
 ↓
Select
 ↓
Save
 ↓
Upload
```

---

# 25. Important beginner rule

When confused, first run:

```powershell
git status
```

Then ask:

1. Which folder am I in?
2. Which branch am I on?
3. What files changed?
4. Are they staged?
5. Have I committed them?
6. Have I pushed them?

---

# 26. Our current project

Local project:

```text
...\AI-ML-Projects\ev-mlops-platform
```

Connected GitHub repository:

```text
https://github.com/aseth83/ev-mlops-platform
```

Primary branch:

```text
main
```

Workflow:

```text
Learn
 ↓
Edit/build
 ↓
Test
 ↓
git status
 ↓
git add
 ↓
git commit
 ↓
git push
 ↓
GitHub evidence
```

---

# Quick Cheat Sheet

```powershell
Get-Location
git status
git branch --show-current
git remote -v
git add README.md
git add .
git commit -m "describe the change"
git push
git pull
git log --oneline
```

---

# One-sentence summary

> Git tracks changes locally; `git add` selects changes, `git commit` saves a checkpoint, and `git push` sends those commits to GitHub.
