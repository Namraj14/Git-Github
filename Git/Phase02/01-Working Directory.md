# 📂 Working Directory

## What is the Working Directory?

The **Working Directory** is the folder on your computer where you create, edit, delete, and organize your project files.

It contains the current version of your project that you are actively working on.

Whenever you make changes to a file, those changes first appear in the **Working Directory**.

---

# Example

Suppose you have the following project:

```text
MyProject/
│
├── index.html
├── style.css
├── app.js
└── README.md
```

This folder (`MyProject`) is your **Working Directory**.

If you edit `app.js`, the changes are made in the Working Directory first.

---

# Types of Files in the Working Directory

Git classifies files into three categories:

## 1. Untracked Files

An **Untracked File** is a file that Git has never seen before.

Git does not monitor or include these files in version control until you explicitly add them.

### Example

You create a new file:

```text
login.js
```

Git has no knowledge of this file yet.

To start tracking it, use:

```bash
git add login.js
```

---

## 2. Tracked Files

A **Tracked File** is a file that Git is already monitoring.

A file becomes tracked after it has been added to Git using `git add` and committed.

Git keeps track of every change made to tracked files.

### Example

```text
app.js
style.css
index.html
```

These files have already been committed, so Git tracks them.

---

## 3. Modified Files

A **Modified File** is a tracked file that has been changed after the last commit.

Git detects that the file has been edited but the latest changes have not yet been staged or committed.

### Example

Suppose `app.js` was committed earlier.

You edit it by adding new code.

Now `app.js` is a **Modified File**.

The changes remain only in the Working Directory until you stage them using:

```bash
git add app.js
```

---

# Working Directory Workflow

```text
Create or Edit File
        │
        ▼
 Working Directory
        │
        ▼
    git add
        │
        ▼
  Staging Area
        │
        ▼
  git commit
        │
        ▼
 Local Repository
```

---

# Check the Status of the Working Directory

Git provides the following command to check the current state of your Working Directory:

```bash
git status
```

### Purpose

This command shows:

* Current branch
* Untracked files
* Modified files
* Staged files
* Whether your working tree is clean

---

# Example Output (Untracked File)

```text
On branch main

Untracked files:
  login.js
```

This means Git has found a new file but is not tracking it yet.

---

# Example Output (Modified File)

```text
On branch main

Changes not staged for commit:
  modified: app.js
```

This means `app.js` has been edited, but the changes have not been staged.

---

# Example Output (Clean Working Directory)

```text
On branch main

nothing to commit, working tree clean
```

This means:

* No modified files
* No untracked files
* No staged changes

Your Working Directory matches the latest commit.

---

# Summary

| File Type     | Description                                                            |
| ------------- | ---------------------------------------------------------------------- |
| **Untracked** | A new file that Git is not tracking.                                   |
| **Tracked**   | A file that Git is monitoring because it has been added and committed. |
| **Modified**  | A tracked file that has been changed since the last commit.            |

---

# Key Points

* The **Working Directory** is where you actively work on your project files.
* Every new file starts as an **Untracked File**.
* After adding and committing a file, it becomes a **Tracked File**.
* Editing a tracked file makes it a **Modified File**.
* Use `git status` to see the current state of your Working Directory and file statuses.
