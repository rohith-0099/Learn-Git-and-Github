# Learn Git & GitHub: A Beginner’s Guide ✨

![Git](https://img.shields.io/badge/Git-Tool-red?logo=git)
![GitHub](https://img.shields.io/badge/GitHub-Platform-black?logo=github)
![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen)
![Last Commit](https://img.shields.io/github/last-commit/rohith-0099/Learn-Git-and-Github)
![Stars](https://img.shields.io/github/stars/rohith-0099/Learn-Git-and-Github?style=social)

This repository is a complete, beginner-friendly guide to **Git** (version control) and **GitHub** (hosting & collaboration). Follow it top-to-bottom for a solid foundation with hands-on commands, visuals, and practical workflows. 🚀

---

## Table of Contents
1. What is Git?
2. Install & Configure Git
3. Git Concepts: Snapshots and the 3 Areas
4. Core Workflow: Add → Commit → Push
5. Branching and Merging
6. Working with GitHub: Clone, Remote, Push, Pull
7. Collaboration: Forks, Pull Requests, and Reviews
8. Undo & Fix: Common Recovery Commands
9. Practical Mini Project: First Repo to First PR
10. Quick Cheatsheet
11. Tips, Conventions, and Best Practices
12. Troubleshooting (Common Errors)

---

## 1) What is Git?

Think of Git as a **time machine for code**. It lets you:
- Save checkpoints of your project (commits)
- Revert to earlier versions if something breaks
- Work with others safely without overwriting work
- See who changed what, when, and why

Git = local version control tool.  
GitHub = cloud host for Git repos + collaboration features (issues, pull requests, reviews, actions).

---

## 2) Install & Configure Git

Install Git:
- Windows: https://git-scm.com/download/win
- macOS (Homebrew):
  ```
  brew install git
  ```
- Linux (Debian/Ubuntu):
  ```
  sudo apt-get update
  sudo apt-get install git
  ```

Set identity (once per machine):
```
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

Optional quality-of-life:
```
git config --global init.defaultBranch main
git config --global core.editor "code --wait"     # VS Code as editor
git config --global pull.rebase false             # merge-based pulls (default)
git config --global color.ui auto                 # colored output
```

Verify:
```
git --version
git config --list
```

---

## 3) Git Concepts: Snapshots and the 3 Areas

Git tracks content through 3 areas:

```
Working Directory  →  Staging Area  →  Local Repository  →  Remote (GitHub)
(edit files)          (git add)        (git commit)         (git push/pull)
```

- Working Directory: your files on disk.
- Staging Area (index): what will go into the next commit.
- Repository (.git): your saved history (commits, branches).

Analogy:
- Working Directory = Countertop (edit)
- Staging Area = Cutting board (choose)
- Repository = Cookbook (history)
- Remote = Online cookbook (share)

---

## 4) Core Workflow: Add → Commit → Push

Initialize a repository (in an empty or existing folder):
```
cd path/to/project
git init
```

Check status:
```
git status
```

Stage and commit:
```
git add <file>            # stage one file
git add .                 # stage everything changed
git commit -m "Describe what you changed"
```

Amend last commit message or add newly staged changes:
```
git commit --amend
```

---

## 5) Branching and Merging

Create and switch:
```
git branch feature/login
git checkout feature/login
# or in one step
git checkout -b feature/login
```

Make changes → add → commit. Then merge into main:
```
git checkout main
git merge feature/login
```

Delete merged branch:
```
git branch -d feature/login     # -D to force delete if not merged
```

View branches and history:
```
git branch
git log --oneline --graph --decorate --all
```

---

## 6) Working with GitHub: Clone, Remote, Push, Pull

Clone an existing repo (download from GitHub):
```
git clone https://github.com/rohith-0099/Learn-Git-and-Github.git
cd Learn-Git-and-Github
```

Link a local repo to a new GitHub repo:
```
# After git init and at least one commit
git remote add origin https://github.com/rohith-0099/Learn-Git-and-Github.git
git push -u origin main
```

Pull latest changes from GitHub:
```
git pull
```

List remotes:
```
git remote -v
```

Change remote URL:
```
git remote set-url origin https://github.com/<user>/<repo>.git
```

---

## 7) Collaboration: Forks, Pull Requests, and Reviews

Typical workflow (contributing to someone else’s repo):
```
1) Fork the repository on GitHub (your account gets a copy).
2) Clone your fork locally.
3) Create a feature branch.
4) Commit changes and push branch to your fork.
5) Open a Pull Request (PR) from your branch to the original repo’s main.
6) Address review comments, push updates.
7) Maintainer merges PR.
```

Commands example:
```
# After forking on GitHub
git clone https://github.com/<your-username>/<repo>.git
cd <repo>

git checkout -b docs/update-readme
# edit files
git add .
git commit -m "Improve README: add course outline and examples"
git push -u origin docs/update-readme
# Open PR on GitHub UI
```

Keep fork up-to-date with upstream:
```
git remote add upstream https://github.com/<original-owner>/<repo>.git
git fetch upstream
git checkout main
git merge upstream/main
git push origin main
```

---

## 8) Undo & Fix: Common Recovery Commands

Unstage (keep changes in working directory):
```
git reset HEAD <file>
```

Discard local changes (dangerous, cannot recover easily):
```
git checkout -- <file>     # for old Git
git restore <file>         # newer Git
```

Change last commit message/content:
```
git commit --amend
```

Move branch pointer (soft/mixed/hard reset):
```
git reset --soft <commit>   # keep staged/working changes
git reset --mixed <commit>  # default, keep working, unstage
git reset --hard <commit>   # discard everything after commit (danger)
```

Revert a commit by creating a new inverse commit:
```
git revert <commit>
```

See history and references:
```
git log --oneline --graph --decorate --all
git reflog
```

---

## 9) Practical Mini Project: First Repo to First PR

Initialize project:
```
mkdir hello-git
cd hello-git
git init
echo "Hello Git!" > hello.txt
git add hello.txt
git commit -m "Add hello.txt"
```

Create GitHub repo and connect:
```
# Create empty repo on GitHub named hello-git (no README)
git branch -M main
git remote add origin https://github.com/<your-username>/hello-git.git
git push -u origin main
```

Create a feature branch and update:
```
git checkout -b feature/update-hello
echo "This is my first branch." >> hello.txt
git add hello.txt
git commit -m "Append branch note to hello.txt"
git push -u origin feature/update-hello
```

Open a Pull Request on GitHub from feature/update-hello → main, review, and merge.  
Pull merged changes locally:
```
git checkout main
git pull
```

---

## 10) Quick Cheatsheet

```
# Setup
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# New repo
git init
git add .
git commit -m "Initial commit"

# Remote/GitHub
git remote add origin <url>
git push -u origin main
git pull
git clone <url>

# Branching
git checkout -b <branch>
git checkout main
git merge <branch>
git branch -d <branch>

# Inspect
git status
git log --oneline --graph --decorate --all
git diff

# Undo
git reset HEAD <file>           # unstage
git restore <file>              # discard changes (newer Git)
git commit --amend              # edit last commit
git revert <commit>             # safe undo with new commit
git reset --hard <commit>       # dangerous reset
```

---

## 11) Tips, Conventions, and Best Practices

- Write clear, imperative commit messages:
  - “Add CONTRIBUTING guide” not “Added” or “Adding”
- Commit small, logical chunks; avoid giant commits.
- Use branches per feature/fix: `feature/…`, `fix/…`, `docs/…`
- Keep main always deployable/green.
- Pull before pushing to reduce conflicts.
- Add `.gitignore` early (e.g., for node_modules, build artifacts).
- Review diffs before committing: `git diff`, `git diff --staged`
- Prefer meaningful PR descriptions with context, screenshots if UI.

---

## 12) Troubleshooting (Common Errors)

“fatal: not a git repository”  
```
# Run inside a repo folder, or initialize first
git init
```

“Updates were rejected because the remote contains work that you do not have locally”  
```
git pull --rebase origin main
# resolve conflicts if any, then:
git push
```

“fatal: remote origin already exists”  
```
git remote -v
git remote set-url origin <url>
```

“nothing to commit, working tree clean” but changes not seen  
- Ensure files are saved and not ignored by `.gitignore`.
- Check you’re on the branch you expect: `git branch`

“Permission denied (publickey)” when pushing via SSH  
- Add SSH key to GitHub or use HTTPS remote URL.

---
