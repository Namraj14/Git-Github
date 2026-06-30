# 🔄 Git Rebase

## What is Git Rebase?

**Git Rebase** is used to **move or replay the commits of one branch on top of another branch**.

Instead of creating a merge commit like `git merge`, rebase creates a **linear (straight) commit history**, making the project history cleaner and easier to read.

---

# Why Do We Need Rebase?

Suppose two developers are working on different branches.

While you're developing a feature, new commits are added to the `main` branch.

Your branch becomes outdated.

Using **Git Rebase**, you can place your feature commits on top of the latest commits from `main`.

This keeps your branch up to date with the latest changes.

---

# How Rebase Works

### Before Rebase

```text id="k8x2wp"
A ─── B ─── C (main)
       \
        D ─── E (feature-login)
```

Here:

* `main` has a new commit **C**.
* `feature-login` still starts from **B**.

---

### Run

```bash id="jlwm9k"
git rebase main
```

---

### After Rebase

```text id="px8t7y"
A ─── B ─── C ─── D' ─── E'
                     ^
              feature-login
```

Notice:

* Commits **D** and **E** are replayed after **C**.
* `D'` and `E'` are **new commits** with new commit hashes.
* The history becomes a straight line.

---

# Why Rebase Creates a Clean Commit History

### Merge History

```text id="jlwm7m"
A ─── B ─── C
       \      \
        D ─── E ── Merge Commit
```

The history contains an extra merge commit.

---

### Rebase History

```text id="jlwm8n"
A ─── B ─── C ─── D' ─── E'
```

The history is linear and easier to understand.

This is why many teams prefer rebasing feature branches before merging them.

---

# Rebase a Branch

## Command

```bash id="jlwm5u"
git rebase main
```

### Purpose

Moves the commits from the current branch so they appear **after the latest commit on `main`**.

### Example

Current branch:

```text id="jlwm4r"
feature-login
```

Run:

```bash id="jlwm6s"
git rebase main
```

Your feature branch is now based on the latest version of `main`.

---

# Interactive Rebase

Interactive Rebase gives you complete control over recent commits.

It allows you to:

* Reorder commits.
* Rename commit messages.
* Combine multiple commits into one (Squash).
* Delete unwanted commits.
* Split a commit into multiple commits.

---

## Command

```bash id="jlwm3t"
git rebase -i HEAD~3
```

### Meaning

* `-i` → Interactive mode.
* `HEAD~3` → The last **3 commits** before the current commit.

Git opens an editor showing something like:

```text id="jlwm2v"
pick a1b2c3 Added Login Page
pick d4e5f6 Fixed Login Bug
pick g7h8i9 Updated CSS
```

You can change the commands:

```text id="jlwm1w"
pick a1b2c3 Added Login Page
reword d4e5f6 Fixed Login Bug
squash g7h8i9 Updated CSS
```

This allows you to modify the commit history before sharing it.

---

# Example Workflow

Current history:

```text id="p2r7yx"
main

A ─── B ─── C

feature-login

A ─── B ─── D ─── E
```

Switch to your feature branch:

```bash id="m7q9vt"
git switch feature-login
```

Rebase onto main:

```bash id="n5x8ku"
git rebase main
```

Result:

```text id="w4z3le"
A ─── B ─── C ─── D' ─── E'
```

Your branch now includes the latest changes from `main`.

---

# Rebase vs Merge

| Rebase                                    | Merge                               |
| ----------------------------------------- | ----------------------------------- |
| Creates a linear commit history.          | Creates a merge commit.             |
| Replays commits on top of another branch. | Combines two branch histories.      |
| Produces a cleaner Git history.           | Preserves the exact branch history. |
| Rewrites commit history.                  | Does not rewrite commit history.    |

---

# Important Note

Because **rebase rewrites commit history**, you should:

* ✅ Use it on **your own local feature branches**.
* ❌ Avoid rebasing commits that have already been pushed and shared with other developers unless your team specifically follows that workflow.

---

# Commands Summary

| Command                | Purpose                                                                  |
| ---------------------- | ------------------------------------------------------------------------ |
| `git rebase main`      | Replays the current branch's commits on top of the latest `main` branch. |
| `git rebase -i HEAD~3` | Starts an interactive rebase for the last three commits.                 |

---

# Best Practices

* Rebase your feature branch before merging it into `main` to keep the history clean.
* Use Interactive Rebase to clean up commit messages and combine small commits before pushing.
* Resolve any conflicts carefully during a rebase.
* Do not rebase commits that have already been shared unless everyone on the team understands the implications.

---

# Summary

| Term                   | Description                                                                   |
| ---------------------- | ----------------------------------------------------------------------------- |
| **Rebase**             | Replays commits from one branch onto another to create a linear history.      |
| **Interactive Rebase** | A mode that lets you edit, reorder, rename, squash, or remove recent commits. |
| **Linear History**     | A straight commit history without unnecessary merge commits.                  |

---

# Key Points

* `git rebase` moves your branch so it starts from the latest commit of another branch.
* Rebase creates a cleaner, linear commit history than merge.
* `git rebase main` updates your current branch with the latest changes from `main`.
* `git rebase -i HEAD~3` opens Interactive Rebase for editing the last three commits.
* Use rebase on local feature branches, and be cautious when working with shared branches because it rewrites commit history.
