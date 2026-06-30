# 🔍 Compare Changes

## What is Comparing Changes?

Git allows you to compare different versions of your files to see **what has changed**.

Instead of manually checking files, Git highlights:

* Lines that were added.
* Lines that were removed.
* Lines that were modified.

This helps you review your changes before committing them.

---

# Difference Between Modified and Committed Code

## Modified Code

**Modified code** refers to changes made in the **Working Directory** that have **not yet been committed**.

These changes exist only on your local machine and can still be edited, staged, or discarded.

### Example

Original file (`app.js`):

```javascript
function login() {
    console.log("Login");
}
```

After editing:

```javascript
function login() {
    console.log("User Login");
}
```

This is **modified code** because it has not been committed yet.

---

## Committed Code

**Committed code** is code that has been permanently saved in the **Local Repository** using a commit.

Once committed, Git records the changes as part of the project's history.

Example:

```bash
git commit -m "Updated login message"
```

Now the modified code becomes part of the repository history.

---

# How Git Compares Changes

Git compares different areas of your project.

```text
Working Directory
        │
        │ git add
        ▼
Staging Area
        │
        │ git commit
        ▼
Local Repository
```

Depending on the command you use, Git compares different locations.

---

# Compare Working Directory with Staging Area

Use:

```bash
git diff
```

### Purpose

Shows the differences between:

* **Working Directory**
* **Staging Area**

It displays changes that have been made **but not yet staged**.

### Example

Suppose `app.js` was committed.

You edit it but haven't staged it yet.

Running:

```bash
git diff
```

Example output:

```diff
- console.log("Login");
+ console.log("User Login");
```

This means:

* `-` represents removed lines.
* `+` represents added lines.

---

# Compare Staging Area with Last Commit

Use:

```bash
git diff --staged
```

### Purpose

Shows the differences between:

* **Staging Area**
* **Last Commit (HEAD)**

It displays changes that have already been staged and are ready to be committed.

### Example

You stage your changes:

```bash
git add app.js
```

Now run:

```bash
git diff --staged
```

Example output:

```diff
- console.log("Login");
+ console.log("User Login");
```

These are the changes that will be included in the next commit.

---

# Difference Between `git diff` and `git diff --staged`

| Command             | Compares                          | Purpose                                              |
| ------------------- | --------------------------------- | ---------------------------------------------------- |
| `git diff`          | Working Directory ↔ Staging Area  | Shows unstaged changes.                              |
| `git diff --staged` | Staging Area ↔ Last Commit (HEAD) | Shows staged changes that are ready to be committed. |

---

# Example Workflow

Suppose you edit `app.js`.

```text
Working Directory (Modified)
```

Run:

```bash
git diff
```

Git shows the unstaged changes.

---

Stage the file:

```bash
git add app.js
```

Now run:

```bash
git diff --staged
```

Git shows the staged changes that will be committed.

Finally, commit the changes:

```bash
git commit -m "Updated login message"
```

Now there are no differences because the changes have been saved in the repository.

---

# Best Practices

* Always review your changes with `git diff` before staging.
* Review staged changes with `git diff --staged` before committing.
* Verify that only the intended changes are included in your commit.
* Use these commands to catch accidental edits before they become part of the repository history.

---

# Summary

| Term                    | Description                                                                      |
| ----------------------- | -------------------------------------------------------------------------------- |
| **Modified Code**       | Changes made in the Working Directory that have not been committed.              |
| **Committed Code**      | Changes permanently saved in the Local Repository.                               |
| **`git diff`**          | Shows unstaged changes by comparing the Working Directory with the Staging Area. |
| **`git diff --staged`** | Shows staged changes by comparing the Staging Area with the last commit.         |

---

# Key Points

* Git can compare changes between different areas of your repository.
* **Modified code** exists in the Working Directory and has not been committed.
* **Committed code** is stored permanently in the Local Repository.
* Use `git diff` to review unstaged changes.
* Use `git diff --staged` to review staged changes before committing.
* Reviewing changes before every commit helps maintain clean and accurate project history.
