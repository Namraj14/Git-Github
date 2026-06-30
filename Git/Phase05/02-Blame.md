# 🔍 Git Blame

## What is Git Blame?

**`git blame`** is a Git command used to identify **who last modified each line of a file**.

For every line in a file, Git displays:

* The commit hash
* The author's name
* The date and time of the change
* The line of code

This helps you understand **who made a change, when it was made, and which commit introduced it**.

---

# Why Do We Need Git Blame?

Imagine you find a bug in your project.

Instead of searching through every commit manually, you can use `git blame` to find:

* Who wrote the code.
* Which commit introduced the change.
* When the change was made.

This makes debugging and understanding the code much easier.

---

# How Git Blame Works

Suppose `app.js` contains:

```javascript
function login() {
    console.log("User Login");
}
```

Running:

```bash
git blame app.js
```

might produce:

```text
4f8c2ab (John Doe 2026-06-29 10:30:12 +0530 1) function login() {
7d2e4f1 (Alice    2026-06-30 09:15:40 +0530 2)     console.log("User Login");
4f8c2ab (John Doe 2026-06-29 10:30:12 +0530 3) }
```

---

# Understanding the Output

```text
4f8c2ab (John Doe 2026-06-29 10:30:12 +0530 1)
```

| Part         | Meaning                           |
| ------------ | --------------------------------- |
| `4f8c2ab`    | Commit hash                       |
| `John Doe`   | Author who last modified the line |
| `2026-06-29` | Date of the change                |
| `10:30:12`   | Time of the change                |
| `1`          | Line number                       |

---

# Command

## View Line-by-Line History

```bash
git blame fileName
```

### Example

```bash
git blame app.js
```

### Purpose

Shows who last modified each line in `app.js`.

---

# Example Workflow

Suppose the project has:

```text
app.js
```

You notice an issue in the following line:

```javascript
console.log("User Login");
```

Run:

```bash
git blame app.js
```

Git shows:

```text
7d2e4f1 Alice console.log("User Login");
```

Now you know:

* Alice made the last change.
* The commit hash is `7d2e4f1`.
* You can inspect that commit using:

```bash
git show 7d2e4f1
```

---

# Common Use Cases

### Find Who Introduced a Bug

Identify who last modified the problematic line.

---

### Understand Code History

See when and why a line was changed.

---

### Review Old Code

Understand the history of legacy code before making changes.

---

### Find the Related Commit

After getting the commit hash, inspect it using:

```bash
git show <commit-hash>
```

---

# Git Blame Workflow

```text
Project File
      │
      ▼
git blame app.js
      │
      ▼
Displays:
• Commit Hash
• Author
• Date
• Line Number
• Code
```

---

# Command Summary

| Command              | Purpose                                      |
| -------------------- | -------------------------------------------- |
| `git blame fileName` | Shows who last modified each line of a file. |

---

# Best Practices

* Use `git blame` to understand code history, not to assign blame to team members.
* Combine `git blame` with `git show` to understand why a change was made.
* Review the commit message before modifying existing code.
* Use it while debugging or investigating unexpected behavior.

---

# Summary

| Term            | Description                                       |
| --------------- | ------------------------------------------------- |
| **Git Blame**   | Shows who last modified each line of a file.      |
| **Commit Hash** | Identifies the commit that last changed the line. |
| **Author**      | The developer who last modified the line.         |

---

# Key Points

* `git blame` displays the last commit responsible for each line in a file.
* It shows the commit hash, author, date, line number, and code.
* It is commonly used for debugging, understanding code history, and tracking changes.
* `git blame` does **not** modify the repository; it is a read-only command.
* You can use the commit hash from `git blame` with `git show` to view the complete details of that commit.
