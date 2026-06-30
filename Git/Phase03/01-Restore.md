# ↩️ Restore

## What is Restore?

The **`git restore`** command is used to **undo changes** before they are committed.

It allows you to:

* Discard unwanted changes in your Working Directory.
* Remove files from the Staging Area without deleting your work.

Since these changes are **not yet committed**, you can safely restore them to a previous state.

---

# Why Use `git restore`?

While working on a project, you may:

* Accidentally modify a file.
* Stage the wrong file.
* Decide you no longer want certain changes.

Instead of editing the file manually, Git allows you to restore it quickly.

---

# Restore a Modified File

Use:

```bash
git restore fileName
```

### Example

Suppose `app.js` originally contains:

```javascript
function login() {
    console.log("Login");
}
```

You accidentally change it to:

```javascript
function login() {
    console.log("Wrong Code");
}
```

To discard these changes:

```bash
git restore app.js
```

### What Happens?

* The file returns to its **last committed version**.
* All uncommitted changes in that file are **lost**.
* The file is removed from the list of modified files.

> **Note:** This action cannot be undone if the changes were never committed.

---

# Restore a Staged File

Use:

```bash
git restore --staged fileName
```

### Example

You stage a file:

```bash
git add app.js
```

Later, you realize you don't want to include it in the next commit.

Run:

```bash
git restore --staged app.js
```

### What Happens?

* The file is removed from the **Staging Area**.
* The file's changes are **not deleted**.
* The changes remain in the **Working Directory** as modified changes.

---

# Difference Between the Two Commands

## `git restore fileName`

Restores the file in the **Working Directory**.

```text
Before

Working Directory (Modified)
        │
        ▼
git restore app.js
        │
        ▼
Working Directory = Last Commit
```

Result:

* Discards uncommitted changes.
* Restores the last committed version.

---

## `git restore --staged fileName`

Removes the file from the **Staging Area**.

```text
Before

Working Directory
        │
        ▼
Staging Area
        │
git restore --staged app.js
        ▼
Working Directory (Modified)
```

Result:

* File is unstaged.
* Changes remain in the Working Directory.

---

# Example Workflow

Suppose you modify `app.js`.

Check the status:

```bash
git status
```

Output:

```text
modified: app.js
```

Discard the changes:

```bash
git restore app.js
```

Now run:

```bash
git status
```

Output:

```text
nothing to commit, working tree clean
```

---

Suppose you stage the file:

```bash
git add app.js
```

Status:

```text
Changes to be committed:
    modified: app.js
```

Remove it from staging:

```bash
git restore --staged app.js
```

Status:

```text
Changes not staged for commit:
    modified: app.js
```

The file is no longer staged, but your changes are still present.

---

# Commands Summary

| Command                         | Purpose                                                                                  |
| ------------------------------- | ---------------------------------------------------------------------------------------- |
| `git restore fileName`          | Discards uncommitted changes and restores the file to its last committed version.        |
| `git restore --staged fileName` | Removes a file from the Staging Area while keeping the changes in the Working Directory. |

---

# Best Practices

* Use `git restore fileName` only when you are certain you no longer need the uncommitted changes.
* Use `git restore --staged fileName` if you staged the wrong file but still want to keep your changes.
* Always check the output of `git status` before and after using `git restore`.

---

# Summary

| Command                         | Affects           | Changes Kept?                                   |
| ------------------------------- | ----------------- | ----------------------------------------------- |
| `git restore fileName`          | Working Directory | ❌ No, changes are discarded.                    |
| `git restore --staged fileName` | Staging Area      | ✅ Yes, changes remain in the Working Directory. |

---

# Key Points

* `git restore` is used to undo changes **before they are committed**.
* `git restore fileName` discards changes in the Working Directory and restores the last committed version.
* `git restore --staged fileName` removes a file from the Staging Area without deleting your work.
* `git status` is useful for verifying the state of your files before and after restoring them.
