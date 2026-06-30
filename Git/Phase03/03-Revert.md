# ↩️ Git Revert

## What is Git Revert?

**`git revert`** is used to **undo the changes introduced by a previous commit by creating a new commit**.

Unlike `git reset`, **Git does not remove the original commit**. Instead, it creates a new commit that reverses the changes made by the specified commit.

This preserves the project's history.

---

# How Does Git Revert Work?

Suppose your commit history is:

```text
Commit A
   │
   ▼
Commit B
   │
   ▼
Commit C ← HEAD
```

You run:

```bash
git revert HEAD
```

Git creates a new commit:

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
Commit D (Reverts Commit C) ← HEAD
```

Notice that:

* Commit C is **still present**.
* Git creates Commit D, which **undoes the changes made in Commit C**.

---

# Why Revert is Safer Than Reset

The biggest difference is that **revert does not rewrite Git history**.

### Git Reset

```text
Commit A
   │
   ▼
Commit B
   │
   ▼
Commit C ← HEAD
```

Run:

```bash
git reset --hard HEAD~1
```

Result:

```text
Commit A
   │
   ▼
Commit B ← HEAD
```

Commit C is removed from the branch history.

---

### Git Revert

```text
Commit A
   │
   ▼
Commit B
   │
   ▼
Commit C ← HEAD
```

Run:

```bash
git revert HEAD
```

Result:

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
Commit D (Undo Commit C) ← HEAD
```

All commits remain in the history.

---

# Why is Revert Safer?

`git revert` is considered safer because:

* It **does not delete commits**.
* It **preserves project history**.
* Other developers' commits are not affected.
* It is safe to use even after commits have been pushed to a shared remote repository.

---

# When Should You Use Revert?

Use `git revert` when:

* You have already pushed a commit to GitHub or another remote repository.
* You need to undo a bug or incorrect change.
* You want to preserve the complete commit history.
* You are working in a team and do not want to rewrite shared history.

---

# When Should You NOT Use Reset Instead?

Suppose your team has already pulled your latest commit.

If you run:

```bash
git reset --hard HEAD~1
```

your local history changes, but your teammates still have the old commit.

This causes history conflicts when pushing or pulling.

Instead, use:

```bash
git revert HEAD
```

Everyone keeps the same commit history, and the unwanted changes are safely undone.

---

# Command

## Revert the Latest Commit

```bash
git revert HEAD
```

### Purpose

* Creates a new commit.
* Reverses the changes introduced by the latest commit.
* Keeps the original commit in the history.

---

# Example

Current history:

```text
Commit 1 → Initial Project
        │
        ▼
Commit 2 → Added Login Page
        │
        ▼
Commit 3 → Added Login Bug ← HEAD
```

Run:

```bash
git revert HEAD
```

Result:

```text
Commit 1 → Initial Project
        │
        ▼
Commit 2 → Added Login Page
        │
        ▼
Commit 3 → Added Login Bug
        │
        ▼
Commit 4 → Revert "Added Login Bug" ← HEAD
```

The login bug is removed, but Commit 3 remains in the history.

---

# Reset vs Revert

| Feature                      | Git Reset | Git Revert                          |
| ---------------------------- | --------- | ----------------------------------- |
| Removes commits from history | ✅ Yes     | ❌ No                                |
| Creates a new commit         | ❌ No      | ✅ Yes                               |
| Rewrites history             | ✅ Yes     | ❌ No                                |
| Safe for shared repositories | ❌ No      | ✅ Yes                               |
| Best for local commits       | ✅ Yes     | ⚠️ Possible but usually unnecessary |
| Best for pushed commits      | ❌ No      | ✅ Yes                               |

---

# Best Practices

* Use **`git reset`** only for local commits that have not been shared.
* Use **`git revert`** for commits that have already been pushed to a remote repository.
* Always read the commit message before reverting to ensure you're undoing the correct commit.
* Review the changes after reverting to confirm the expected result.

---

# Summary

| Command           | Purpose                                                                                                                |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------- |
| `git revert HEAD` | Creates a new commit that reverses the changes made by the latest commit while preserving the original commit history. |

---

# Key Points

* `git revert` undoes changes by **creating a new commit**.
* It does **not** delete or modify existing commits.
* It preserves the complete Git history.
* It is safer than `git reset` because it does not rewrite history.
* Use `git revert` when undoing commits that have already been pushed to a shared repository.
