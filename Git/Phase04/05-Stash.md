# 📦 Git Stash

## What is Git Stash?

**Git Stash** is a feature that allows you to **temporarily save your unfinished changes** without committing them.

It removes your current changes from the **Working Directory** and stores them in a special area called the **stash**.

Later, you can restore those changes whenever you're ready to continue working.

---

# Why Do We Need Git Stash?

Imagine you're working on a feature, but before you finish, your manager asks you to fix an urgent production bug.

Your current work is incomplete, and you don't want to commit half-finished code.

Instead of creating an unnecessary commit, you can use **Git Stash**.

Example:

```text id="5y2i1j"
Current Work
│
├── Login Page (Incomplete)
├── Validation (Incomplete)
└── Forgot Password (Incomplete)
```

You need to switch to another branch immediately.

Run:

```bash id="bqtjlwm"
git stash
```

Your unfinished work is saved, and your Working Directory becomes clean.

---

# How Git Stash Works

```text id="g4mksu"
Working Directory
        │
        ▼
   git stash
        │
        ▼
 Stash Storage
        │
        ▼
Clean Working Directory
```

When you're ready:

```text id="jlwm81"
Stash Storage
      │
      ▼
 git stash pop
      │
      ▼
Working Directory
```

---

# Save Unfinished Work

## Command

```bash id="3v5m2g"
git stash
```

### Purpose

* Saves all modified tracked files.
* Removes those changes from the Working Directory.
* Returns the repository to the last committed state.

### Example

Before:

```text id="7u3q2r"
modified: app.js
modified: login.js
```

Run:

```bash id="u0r9nh"
git stash
```

Result:

* Changes are saved.
* Working Directory becomes clean.

---

# Restore the Latest Stash

## Command

```bash id="jlwm9f"
git stash pop
```

### Purpose

* Restores the most recently saved stash.
* Removes that stash entry from the stash list.

### Example

Run:

```bash id="q8cp7v"
git stash pop
```

Result:

* Your unfinished changes return to the Working Directory.
* The applied stash is deleted from stash storage.

---

# View All Stashes

## Command

```bash id="k7r1px"
git stash list
```

### Purpose

Displays all saved stashes.

### Example Output

```text id="jlwm3x"
stash@{0}: WIP on feature-login
stash@{1}: WIP on feature-payment
stash@{2}: WIP on main
```

Here:

* `stash@{0}` → Most recent stash.
* `stash@{1}` → Second most recent stash.
* `stash@{2}` → Third most recent stash.

---

# Example Workflow

Suppose you're working on the `feature-login` branch.

Current status:

```text id="g0wsyq"
Modified:
login.js
style.css
```

Check status:

```bash id="jlwm4m"
git status
```

Save the changes:

```bash id="jlwm5n"
git stash
```

Now:

```bash id="8smfyd"
git status
```

Output:

```text id="jlwm6p"
nothing to commit, working tree clean
```

Switch to another branch and complete your work.

Later, return to the original branch and restore the changes:

```bash id="jlwm7q"
git stash pop
```

Your unfinished work is back.

---

# Stash Workflow

```text id="d3h8wn"
Modify Files
      │
      ▼
git stash
      │
      ▼
Changes Stored Safely
      │
      ▼
Switch Branch
      │
      ▼
Finish Other Work
      │
      ▼
Return
      │
      ▼
git stash pop
      │
      ▼
Continue Development
```

---

# Commands Summary

| Command          | Purpose                                                       |
| ---------------- | ------------------------------------------------------------- |
| `git stash`      | Saves unfinished changes and cleans the Working Directory.    |
| `git stash pop`  | Restores the latest stash and removes it from the stash list. |
| `git stash list` | Displays all saved stashes.                                   |

---

# Best Practices

* Use `git stash` when you need to switch tasks quickly without committing incomplete work.
* Use stash for **temporary** storage, not as a long-term backup.
* Check `git stash list` before applying a stash if you have multiple saved stashes.
* After using `git stash pop`, verify your changes with `git status`.

---

# Summary

| Term                 | Description                                                      |
| -------------------- | ---------------------------------------------------------------- |
| **Git Stash**        | Temporarily stores unfinished changes without creating a commit. |
| **`git stash`**      | Saves current changes and cleans the Working Directory.          |
| **`git stash pop`**  | Restores the latest stash and removes it from stash storage.     |
| **`git stash list`** | Lists all saved stashes.                                         |

---

# Key Points

* Git Stash is used to temporarily save unfinished work.
* It allows you to switch branches without committing incomplete changes.
* `git stash` saves your changes and restores a clean Working Directory.
* `git stash pop` brings back the latest stashed changes and removes that stash from the list.
* `git stash list` lets you view all available stashes.
* Stash is ideal for short-term interruptions, such as fixing urgent bugs or reviewing another branch.
