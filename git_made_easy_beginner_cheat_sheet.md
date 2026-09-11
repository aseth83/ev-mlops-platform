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
git push   -u   origin   main
   │        │      │       │
   │        │      │       └─ local branch to push
   │        │      │
   │        │      └───────── remote repository nickname
   │        │
   │        └──────────────── remember the relationship
   │
   └───────────────────────── send commits to remote

   1. git push

This means:

Send commits from my local Git repository to a remote Git repository.

Before pushing, your commit exists only locally:
YOUR COMPUTER

main
 │
 └── Commit A

 GitHub may still be empty.

After pushing:

YOUR COMPUTER              GITHUB

main                       main
 │                          │
 └── Commit A ───────────►  └── Commit A

2. origin

origin is just a nickname.

When you cloned:
git clone https://github.com/aseth83/ev-mlops-platform.git
Git automatically created:
origin

Friday 7:55 AM

90_day_AI_ML_MLOps_curriculum.md
File
Learning AI-ML, see the attached md, please check and share your suggestions

That warning is normal on Windows and does not mean anything failed.

Git successfully staged your files with:

git add .
The warning:

LF will be replaced by CRLF the next time Git touches it
is about line endings.

Windows traditionally uses:

CRLF
while Linux/macOS commonly use:

LF
Your Markdown file currently uses LF, and Git is telling you that your Windows setup may convert it to CRLF in your working copy later.

Think of it like this:

Same text:

Hello
World
can internally be stored as either:

Linux/macOS:
Hello<LF>
World<LF>
or:

Windows:
Hello<CR><LF>
World<CR><LF>
For our project, you can safely ignore this warning. It does not damage the Markdown file.

Now let's verify what you staged:

git status
You should probably see both files under:

Changes to be committed:
such as:

new file: README.md
new file: git_made_easy_beginner_cheat_sheet.md
Then we can create our first commit.

Because you're committing both the project README and Git learning notes, I'd use:

git commit -m "docs: add project README and Git beginner guide"
Notice the flow you have now completed:

Created files
     ↓
git status
     ↓
Untracked files
     ↓
git add .
     ↓
Staged files
     ↓
git commit
     ↓
First Git checkpoint
One more useful point: git add . means stage all changed/untracked files under the current repository location, whereas earlier:

git add README.md
staged only one specific file.

For now, run:

git status
and then:

git commit -m "docs: add project README and Git beginner guide"
If Git asks you to configure your user.name or user.email, paste that message here before changing anything, and I’ll explain what it means.


PS C:\Users\ASETH1\OneDrive - Volvo Cars\Documents\WORK\Knowledge\AUTOMATION\SCRIPTS\AI\AI-ML-Projects\ev-mlops-platform> git status
On branch main
Your branch is based on 'origin/main', but the upstream is gone.
  (use "git branch --unset-upstream" to fixup)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   git_made_easy_beginner_cheat_sheet.md

This output makes sense given that you cloned an empty GitHub repository. Nothing is broken.

The key message is:

Your branch is based on 'origin/main', but the upstream is gone.
Here, upstream means:

“Which remote branch should my local branch main normally push to and pull from?”

Ideally, after setup we want:

Local                            GitHub

main  ───────────────────────►   origin/main
        git push

main  ◄───────────────────────   origin/main
        git pull
But your GitHub repository was completely empty when you cloned it. So Git created your local main, but there is not yet a real main branch on GitHub containing a commit.

Conceptually, right now:

YOUR COMPUTER

main
 └── no commit yet


GITHUB

ev-mlops-platform
 └── empty repository
     no main commit yet
That is why Git says the upstream origin/main is “gone.”

Don't run git branch --unset-upstream
Git suggests:

git branch --unset-upstream
but we don't need that for our situation.

When we make the first commit and run:

git push -u origin main
Git will create main on GitHub and establish the proper connection:

local main
     │
     │ -u establishes tracking
     ▼
origin/main
After that, normal commands become simply:

git push
and:

git pull
There is one other thing in your output that I want us to check.

Currently Git says only this is staged:

new file: git_made_easy_beginner_cheat_sheet.md
But we also wanted:

README.md
So before committing, run:

dir
You should ideally see:

README.md
git_made_easy_beginner_cheat_sheet.md
If README.md is there, run:

git add README.md
Then:

git status
We want to reach:

Changes to be committed:

    new file: README.md
    new file: git_made_easy_beginner_cheat_sheet.md
Then create your first commit:

git commit -m "docs: add project README and Git beginner guide"
And finally:

git push -u origin main
That first push is particularly important. The -u means approximately:

Push my local main to origin/main, and remember that these two branches belong together.

After that:

LOCAL                              REMOTE

main ────────────────────────────► origin/main
              push

main ◄──────────────────────────── origin/main
              pull
So your warning is actually a useful consequence of learning Git with a genuinely empty repository. Once we make and push the first commit, it should disappear.


explain more on that git push -u origin main and where have you added this in git_made_easy_beginner_cheat_sheet?

Yes. In the Git guide I created, this command is already covered under:

Section 17 — git push

The file currently contains:

git push -u origin main
with the explanation that it means:

Send my local main branch commits to the GitHub repository called origin.

It also says that -u remembers this connection for future pushes.

What is not yet explained deeply enough in the cheat sheet is the exact relationship between main, origin, origin/main, and -u. Here is the fuller explanation.

Break the command into four pieces
git push -u origin main
means:

git push   -u   origin   main
   │        │      │       │
   │        │      │       └─ local branch to push
   │        │      │
   │        │      └───────── remote repository nickname
   │        │
   │        └──────────────── remember the relationship
   │
   └───────────────────────── send commits to remote
1. git push
This means:

Send commits from my local Git repository to a remote Git repository.

Before pushing, your commit exists only locally:

YOUR COMPUTER

main
 │
 └── Commit A
GitHub may still be empty.

After pushing:

YOUR COMPUTER              GITHUB

main                       main
 │                          │
 └── Commit A ───────────►  └── Commit A
2. origin
origin is just a nickname.

When you cloned:
git clone https://github.com/aseth83/ev-mlops-platform.git
Git automatically created: origin as the nickname for: https://github.com/aseth83/ev-mlops-platform.git
You proved this earlier with:
in powershell
git remote -v

which showed: 
origin  https://github.com/aseth83/ev-mlops-platform.git (fetch)
origin  https://github.com/aseth83/ev-mlops-platform.git (push)

So mentally:
origin
   =
https://github.com/aseth83/ev-mlops-platform.git

# 3. main
This part means:

Push my local branch called main.

You already confirmed:

On branch main

So:
at powershell
git push origin main

means:

Take the commits from my local main branch and send them to the repository called origin.

If GitHub does not yet have a main branch, Git creates it there.

That is exactly relevant in your case because your GitHub repository was empty.


# 4. What -u actually does

This is the important part.

-u is short for:

--set-upstream

So:

git push -u origin main

means:

Push my local main to origin/main, and remember that these two branches are connected.

Before:

LOCAL                     GITHUB

main                      no branch yet

After:

LOCAL                     GITHUB

main  ─────────────────►  main
          push

local main now tracks origin/main

Git internally now remembers approximately:

local branch:
main

tracks:
origin/main

This is why your first push commonly uses:

git push -u origin main

but future pushes can simply use:

git push

Git already knows:

current local branch = main
remote = origin
remote branch = main

Without -u, you could push successfully:

git push origin main

but Git might not establish that default tracking relationship.

Then next time you may again need to specify:

git push origin main

With -u, you're effectively saying:

Remember this destination.

# What is origin/main?

This is where terminology becomes confusing.

You have:

main

and:

origin/main

They are not the same thing.

main = your local branch.

origin/main = Git's reference to the main branch on the remote repository called origin.

Think:

main
│
└── My local main branch

origin/main
│
└── main branch associated with GitHub/origin

After everything is synchronized:

LOCAL                            REMOTE

main                             origin/main
 │                                   │
 ▼                                   ▼
Commit A                         Commit A

Then you make another local commit:

LOCAL                            REMOTE

main                             origin/main
 │                                   │
 ▼                                   ▼
Commit B
 │
Commit A                         Commit A

Now local main is one commit ahead.

Run:
git push

and:

LOCAL                            REMOTE

main                             origin/main
 │                                   │
 ▼                                   ▼
Commit B                         Commit B
 │                               │
Commit A                         Commit A

# Why you saw this warning earlier

You saw:

Your branch is based on 'origin/main',
but the upstream is gone.

That happened because you cloned an empty repository.

There was no actual committed main branch on GitHub yet.

So your situation was roughly:

LOCAL

main
 │
 └── waiting for first commit


GITHUB

ev-mlops-platform
 │
 └── empty

After your first commit and:

# git push -u origin main

you will establish:

Local main
    ↕
origin/main
    ↕
GitHub main

and that unusual empty-repository situation should be resolved.

The easiest way to remember it
# git push -u origin main = Push my local main branch to GitHub (origin) and remember that connection for next time.

Then later:
# git push
is enough.

## REMEMBER ##
git push   = send commits to GitHub
-u         = remember the connection
origin     = nickname for your GitHub repository
main       = your local branch
##
So the full meaning is:
Send my local main branch to the GitHub repository called origin, create/update its main branch, and remember that relationship.
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


git add git_made_easy_beginner_cheat_sheet.md
git commit -m "docs: expand Git push and upstream explanation"
git status
git push -u origin main
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
