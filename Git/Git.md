# Git Complete Guide 🚀

## Table of Contents

1. What is Git?
2. Why Git?
3. Git vs GitHub
4. Git Installation
5. Configure Git
6. Create Repository
7. Git Workflow
8. Important Commands
9. Branching
10. Merging
11. Merge Conflicts
12. Stashing
13. Remote Repository
14. Clone Repository
15. Push & Pull
16. Fetch vs Pull
17. Rebase
18. Cherry Pick
19. Reset vs Revert
20. Tags
21. Git Ignore
22. Git Log
23. Git Aliases
24. Git Best Practices
25. Real Time Workflow
26. Interview Questions

---

# What is Git?

Git is a **Distributed Version Control System (DVCS)** used to track changes in source code.

It helps developers:

- Track code history
- Collaborate with team members
- Restore previous versions
- Create multiple branches
- Merge work safely

---

# Why Git?

Without Git

```
project
|
|-- code_v1
|-- code_v2
|-- code_final
|-- code_final_latest
|-- code_final_latest_new
```

Confusing 😅

With Git

```
Project
|
|-- Current Code
|
Git stores complete history
```

Every change is stored permanently.

---

# Git vs GitHub

| Git | GitHub |
|------|---------|
| Version Control Tool | Cloud Repository |
| Installed locally | Works online |
| Tracks changes | Stores repositories |
| Command Line | Website |

Think of it like:

Git = Microsoft Word

GitHub = Google Drive

---

# Install Git

Download from

https://git-scm.com

Verify installation

```bash
git --version
```

Example

```
git version 2.48.1
```

---

# Configure Git

Tell Git who you are.

```bash
git config --global user.name "John Doe"
```

```bash
git config --global user.email "john@gmail.com"
```

Check configuration

```bash
git config --list
```

---

# Create Repository

Navigate to project

```bash
cd MyProject
```

Initialize Git

```bash
git init
```

Output

```
Initialized empty Git repository
```

Git creates

```
.git
```

This hidden folder stores entire history.

---

# Git Workflow

```
Working Directory

↓

Staging Area

↓

Local Repository

↓

Remote Repository (GitHub)
```

---

# Working Directory

Where you write code.

```
App.js

index.html

style.css
```

Nothing is tracked yet.

---

# Staging Area

Add files to staging.

```bash
git add App.js
```

or

```bash
git add .
```

Git now prepares files for commit.

---

# Commit

Save snapshot.

```bash
git commit -m "Added login page"
```

Commit = Save Point

---

# Check Status

```bash
git status
```

Possible outputs

```
Modified

Deleted

Untracked

Staged
```

---

# Git Log

Shows commit history.

```bash
git log
```

Compact version

```bash
git log --oneline
```

Example

```
a12bc45 Added Login

c87de91 Fixed Bug

d123abc Initial Commit
```

---

# View Changes

```bash
git diff
```

Compare staged changes

```bash
git diff --staged
```

---

# Remove from Stage

```bash
git restore --staged file.txt
```

---

# Delete File

```bash
git rm file.txt
```

---

# Rename File

```bash
git mv old.txt new.txt
```

---

# Branching

Create new branch

```bash
git branch feature-login
```

View branches

```bash
git branch
```

Current branch

```
* main
```

Switch branch

```bash
git checkout feature-login
```

Modern command

```bash
git switch feature-login
```

Create and switch

```bash
git checkout -b feature-login
```

or

```bash
git switch -c feature-login
```

---

# Merge Branch

Go to main

```bash
git switch main
```

Merge

```bash
git merge feature-login
```

---

# Merge Conflict

Occurs when two branches edit same line.

Example

Branch A

```
Name = John
```

Branch B

```
Name = David
```

Git cannot decide.

You manually edit

```
Name = John David
```

Then

```bash
git add .
```

```bash
git commit
```

Conflict resolved.

---

# Git Ignore

Ignore unnecessary files.

Create

```
.gitignore
```

Example

```
node_modules/

.env

*.log

dist/

coverage/
```

---

# Stashing

Save unfinished work temporarily.

```bash
git stash
```

View stash

```bash
git stash list
```

Restore

```bash
git stash pop
```

Delete stash

```bash
git stash drop
```

---

# Undo Last Commit

Keep changes

```bash
git reset --soft HEAD~1
```

Remove staging

```bash
git reset --mixed HEAD~1
```

Delete everything

```bash
git reset --hard HEAD~1
```

⚠ Never use hard reset unless absolutely sure.

---

# Revert

Undo without deleting history.

```bash
git revert HEAD
```

Safe for shared repositories.

---

# Reset vs Revert

| Reset | Revert |
|--------|---------|
| Removes history | Preserves history |
| Dangerous | Safe |
| Local use | Shared repositories |

---

# Cherry Pick

Copy one commit.

```bash
git cherry-pick commitID
```

Useful when only one fix is needed.

---

# Rebase

Moves commits onto another branch.

```
Before

A

↓

B

↓

Feature
```

After

```
A

↓

B

↓

Latest Main

↓

Feature Commit
```

Command

```bash
git rebase main
```

Produces cleaner history.

---

# Tags

Mark releases.

Create

```bash
git tag v1.0
```

List

```bash
git tag
```

Push tag

```bash
git push origin v1.0
```

---

# Remote Repository

Connect GitHub.

```bash
git remote add origin https://github.com/user/project.git
```

View remotes

```bash
git remote -v
```

---

# Clone Repository

```bash
git clone https://github.com/user/project.git
```

Downloads entire project.

---

# Push Changes

```bash
git push origin main
```

---

# Pull Changes

```bash
git pull origin main
```

Downloads + merges.

---

# Fetch

```bash
git fetch
```

Downloads only.

Does NOT merge.

---

# Pull vs Fetch

| Pull | Fetch |
|------|--------|
| Download | Download |
| Merge | No Merge |

---

# Remove Branch

Local

```bash
git branch -d feature-login
```

Remote

```bash
git push origin --delete feature-login
```

---

# Git Aliases

Example

```bash
git config --global alias.st status
```

Now

```bash
git st
```

instead of

```bash
git status
```

---

# Useful Commands

```bash
git status
```

```bash
git add .
```

```bash
git commit -m "message"
```

```bash
git push
```

```bash
git pull
```

```bash
git log --oneline
```

```bash
git branch
```

```bash
git switch branchName
```

```bash
git merge branch
```

```bash
git stash
```

```bash
git stash pop
```

---

# Complete Workflow

```
Write Code

↓

git status

↓

git add .

↓

git commit -m "Added feature"

↓

git push

↓

Team Pulls

↓

Continue Development
```

---

# Best Practices

✅ Commit frequently

✅ Use meaningful commit messages

✅ Pull before pushing

✅ Create feature branches

✅ Never commit passwords

✅ Use .gitignore

✅ Review code before commit

✅ Keep commits small

---

# Common Commit Messages

```
Added Login Page

Fixed Validation Bug

Updated README

Refactored Apex Trigger

Improved LWC Performance

Removed Unused Code

Added Test Class
```

---

# Real-Time Workflow Example

Developer A

```
git checkout -b feature-login

Write Code

git add .

git commit -m "Created Login"

git push origin feature-login
```

Developer B

```
git pull origin main

Create another feature

Commit

Push
```

After review

```
Merge feature-login

Delete feature branch
```

---

# Interview Questions

### What is Git?

A distributed version control system.

---

### What is a Commit?

A snapshot of project at a specific time.

---

### Difference between Git and GitHub?

Git tracks code locally.

GitHub hosts repositories online.

---

### Difference between Fetch and Pull?

Fetch downloads.

Pull downloads and merges.

---

### Difference between Reset and Revert?

Reset removes commits.

Revert creates a new commit that undoes previous changes.

---

### What is Staging Area?

Temporary area before committing changes.

---

### What is Merge Conflict?

When Git cannot automatically combine changes.

---

### What is HEAD?

HEAD points to the current commit you're working on.

---

### What is Branch?

An independent line of development.

---

### What is Rebase?

Moves or reapplies commits onto another base commit to create a cleaner history.

---

### What is Cherry Pick?

Copies a specific commit from one branch to another.

---

### What is .gitignore?

A file listing files and folders Git should not track.

---

### Git Workflow Summary

```
Working Directory
        │
        ▼
git add .
        │
        ▼
Staging Area
        │
git commit
        │
        ▼
Local Repository
        │
git push
        │
        ▼
GitHub Repository
```

---

# Conclusion

Git is one of the most essential tools for software developers. Mastering Git means understanding how to:
- Track changes
- Create and merge branches
- Collaborate with teams
- Resolve conflicts
- Manage commit history
- Safely deploy code through version control

Practice these commands regularly in a sample project to become proficient with Git.
