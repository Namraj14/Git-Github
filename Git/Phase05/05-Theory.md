# 🚀 Advanced Git Topics

After learning the Git basics (commits, branches, merge, rebase, stash, tags, etc.), these advanced topics help you work more efficiently in real-world projects.

---

# 1. Interactive Rebase

## What is Interactive Rebase?

**Interactive Rebase** allows you to modify your commit history before sharing it with others.

Unlike a normal rebase, Interactive Rebase lets you:

* Reorder commits.
* Rename commit messages.
* Squash multiple commits into one.
* Split a commit into multiple commits.
* Remove unwanted commits.

It is commonly used to clean up a feature branch before merging it into the main branch.

---

## Why Use Interactive Rebase?

Suppose your commit history is:

```text
Added Login Page
Fixed Typo
Updated CSS
Fixed Validation
Changed Button Color
```

Instead of keeping five small commits, you can combine them into:

```text
Added Login Feature
```

This creates a clean and meaningful commit history.

---

## Command

```bash
git rebase -i HEAD~3
```

### Meaning

* `-i` → Interactive mode.
* `HEAD~3` → Opens the last three commits for editing.

Example:

```text
pick a1b2c3 Added Login
pick d4e5f6 Fixed CSS
pick g7h8i9 Updated Validation
```

You can change it to:

```text
pick a1b2c3 Added Login
squash d4e5f6 Fixed CSS
squash g7h8i9 Updated Validation
```

---

## Best Practices

* Use Interactive Rebase on your own feature branch.
* Avoid rebasing commits that have already been pushed to a shared repository.

---

# 2. Git Hooks

## What are Git Hooks?

**Git Hooks** are scripts that Git automatically executes when certain events occur.

Examples of events:

* Before a commit.
* After a commit.
* Before pushing.
* After merging.

Hooks help automate repetitive tasks.

---

## Why Use Git Hooks?

Suppose your team requires:

* Code formatting.
* Unit tests.
* Linting.

Instead of asking every developer to remember these steps, a Git Hook runs them automatically.

Example:

```text
git commit
      │
      ▼
Run Tests
      │
      ▼
Tests Pass
      │
      ▼
Commit Created
```

If the tests fail, the commit can be blocked.

---

## Common Hooks

| Hook         | Purpose                                     |
| ------------ | ------------------------------------------- |
| `pre-commit` | Runs before creating a commit.              |
| `commit-msg` | Validates the commit message.               |
| `pre-push`   | Runs before pushing to a remote repository. |
| `post-merge` | Runs after a merge completes.               |

---

## Location

Hooks are stored inside:

```text
.git/hooks/
```

---

# 3. Git Submodules

## What is a Git Submodule?

A **Git Submodule** allows you to include one Git repository inside another Git repository.

Each repository keeps its own history independently.

---

## Why Use Submodules?

Suppose two projects use the same authentication library.

Instead of copying the library into both projects, you can add it as a submodule.

Example:

```text
Main Project
│
├── src/
├── docs/
└── authentication-library/  ← Submodule
```

If the authentication library is updated, each project can update to the required version.

---

## Command

Add a submodule:

```bash
git submodule add <repository-url>
```

Initialize submodules after cloning:

```bash
git submodule update --init
```

---

## Benefits

* Code reuse.
* Independent versioning.
* Easier maintenance.

---

# 4. Git Worktrees

## What is a Git Worktree?

A **Git Worktree** allows you to have multiple working directories connected to the same Git repository.

Normally, one repository can have only one checked-out branch.

With Worktrees, you can work on multiple branches simultaneously without creating another clone.

---

## Why Use Worktrees?

Suppose you're working on:

* `feature-login`

Suddenly, a production bug needs fixing.

Without Worktrees:

* Stash changes.
* Switch branches.
* Fix bug.
* Switch back.

With Worktrees:

```text
Main Repository

Branch: feature-login

↓

New Worktree

Branch: hotfix
```

Now both branches are available at the same time.

---

## Command

Create a worktree:

```bash
git worktree add ../hotfix hotfix
```

List worktrees:

```bash
git worktree list
```

---

## Benefits

* No need to stash unfinished work.
* Work on multiple branches simultaneously.
* Faster than cloning the repository again.

---

# 5. Git LFS (Large File Storage)

## What is Git LFS?

**Git LFS (Large File Storage)** is an extension that manages large files efficiently.

Instead of storing large files directly in Git, Git LFS stores small pointer files in the repository while keeping the actual files in separate LFS storage.

---

## Why Do We Need Git LFS?

Git works best with text files.

Large files such as:

* Videos.
* Images.
* Audio files.
* Machine Learning models.
* Game assets.

can make the repository very large and slow.

Git LFS solves this problem.

---

## How Git LFS Works

Without Git LFS:

```text
Repository

video.mp4 (500 MB)
```

With Git LFS:

```text
Repository

video.mp4 (Pointer File)

↓

Large File Storage

video.mp4 (500 MB)
```

---

## Common Commands

Install Git LFS:

```bash
git lfs install
```

Track a file type:

```bash
git lfs track "*.psd"
```

Track videos:

```bash
git lfs track "*.mp4"
```

---

## Benefits

* Smaller Git repository.
* Faster cloning.
* Better performance.
* Efficient handling of large binary files.

---

# Summary

| Topic                  | Purpose                                                        |
| ---------------------- | -------------------------------------------------------------- |
| **Interactive Rebase** | Clean, edit, reorder, squash, or rename commits.               |
| **Git Hooks**          | Automate tasks during Git operations.                          |
| **Git Submodules**     | Include one Git repository inside another.                     |
| **Git Worktrees**      | Work on multiple branches simultaneously using one repository. |
| **Git LFS**            | Efficiently manage and version large files.                    |

---

# Key Points

* **Interactive Rebase** helps maintain a clean and readable commit history.
* **Git Hooks** automate quality checks and workflows during Git operations.
* **Git Submodules** allow multiple projects to share a repository while maintaining independent histories.
* **Git Worktrees** let you work on multiple branches at the same time without creating extra clones.
* **Git LFS** improves Git's performance by storing large files outside the normal Git object database while keeping lightweight references in the repository.
