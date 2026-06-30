# 📜 Git History

## What is Git History?

**Git History** is a record of every commit made in a repository.

Each time you create a commit, Git stores information such as:

* The commit hash
* The commit message
* The author
* The date and time
* The snapshot of the project

Git History allows you to see how your project has evolved over time.

---

# Example

Suppose you made these commits:

```text
Commit 1 → Initial Project Setup
        │
        ▼
Commit 2 → Added Login Page
        │
        ▼
Commit 3 → Fixed Login Validation
        │
        ▼
Commit 4 → Updated Dashboard
```

This sequence of commits is your **Git History**.

---

# What is HEAD?

**HEAD** is a special pointer in Git that points to the **current commit** you are working on.

Whenever you create a new commit, **HEAD automatically moves to that latest commit**.

Think of HEAD as a bookmark that tells Git:

> "This is the current position in the repository."

---

# Example

```text
Commit A
   │
   ▼
Commit B
   │
   ▼
Commit C ← HEAD
```

Here, `HEAD` points to **Commit C**, which is the latest commit.

After creating another commit:

```text
Commit A
   │
   ▼
Commit B
   │
   ▼
Commit C
   │
   ▼
Commit D ← HEAD
```

HEAD automatically moves to **Commit D**.

---

# What is the Current Commit?

The **Current Commit** is the commit that **HEAD** is pointing to.

It represents the latest version of your project that Git is currently using.

Whenever you:

* View files
* Create new commits
* Create branches

Git starts from the current commit.

---

# View Commit History

Use the following command:

```bash
git log
```

### Purpose

Displays detailed information about every commit, including:

* Commit hash
* Author
* Date
* Commit message

### Example Output

```text
commit 4f8c2ab8f6d....

Author: John Doe

Date: Mon Jun 29 10:30:12 2026

    Added Login Page

commit 9a72bc51d4....

Author: John Doe

Date: Mon Jun 28 04:15:20 2026

    Initial Project Setup
```

The most recent commit appears first.

---

# View Short Commit History

Use:

```bash
git log --oneline
```

### Purpose

Displays each commit in a compact format.

### Example Output

```text
4f8c2ab Added Login Page
9a72bc5 Initial Project Setup
```

Here:

* `4f8c2ab` → Short commit hash
* `Added Login Page` → Commit message

This command is useful when you want a quick overview of the project's history.

---

# View Details of the Current Commit

Use:

```bash
git show
```

### Purpose

Displays detailed information about the latest commit (the commit pointed to by **HEAD**).

It shows:

* Commit hash
* Author
* Date
* Commit message
* Changes made in that commit (diff)

### Example Output

```text
commit 4f8c2ab8f6d....

Author: John Doe

Date: Mon Jun 29 10:30:12 2026

    Added Login Page

+ Added login.html
+ Added login.css
+ Updated app.js
```

---

# Git History Workflow

```text
Commit 1
   │
   ▼
Commit 2
   │
   ▼
Commit 3
   │
   ▼
Commit 4 ← HEAD (Current Commit)
```

---

# Commands Summary

| Command             | Purpose                                                                                    |
| ------------------- | ------------------------------------------------------------------------------------------ |
| `git log`           | Displays the complete commit history with detailed information.                            |
| `git log --oneline` | Displays the commit history in a short, one-line format.                                   |
| `git show`          | Displays detailed information about the current (HEAD) commit, including the changes made. |

---

# Best Practices

* Review commit history regularly using `git log`.
* Use `git log --oneline` for a quick overview of commits.
* Use `git show` to inspect the details of the latest commit before sharing or debugging.
* Write meaningful commit messages so your Git history is easy to understand.

---

# Summary

| Term               | Description                                                 |
| ------------------ | ----------------------------------------------------------- |
| **Git History**    | A chronological record of all commits in a repository.      |
| **HEAD**           | A special pointer that always points to the current commit. |
| **Current Commit** | The commit currently referenced by HEAD.                    |

---

# Key Points

* Git History stores every commit made in a repository.
* Each commit contains a snapshot of your project along with metadata like the author, date, commit hash, and message.
* **HEAD** always points to the current (latest) commit on your active branch.
* `git log` shows the complete commit history.
* `git log --oneline` provides a concise view of the commit history.
* `git show` displays detailed information about the current commit and the changes introduced in it.
