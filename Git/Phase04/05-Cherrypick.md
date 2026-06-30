# 🍒 Git Cherry-pick

## What is Git Cherry-pick?

**Git Cherry-pick** is used to **copy a specific commit from one branch and apply it to another branch**.

Instead of merging an entire branch, Git copies **only the selected commit**.

This is useful when you need just one change from another branch.

---

# Why Do We Need Cherry-pick?

Suppose you have two branches:

* `main`
* `feature-login`

The `feature-login` branch has several commits:

```text id="f8t9rp"
Commit A → Initial Project
Commit B → Added Login Page
Commit C → Fixed Login Bug
Commit D → Updated CSS
```

You only want **Commit C** (the bug fix) in the `main` branch.

Instead of merging the entire branch, you can use **Git Cherry-pick** to copy only that commit.

---

# How Cherry-pick Works

Before:

```text id="y1jd6u"
main

A ─── B

feature-login

A ─── B ─── C ─── D
```

Cherry-pick Commit C:

```text id="o2we8k"
git cherry-pick C
```

After:

```text id="1j5nrv"
main

A ─── B ─── C'

feature-login

A ─── B ─── C ─── D
```

> **Note:** `C'` is a **new commit** with the same changes as `C` but a **different commit hash**.

---

# When Should You Use Cherry-pick?

Use `git cherry-pick` when:

* You need only one specific commit from another branch.
* You want to copy a bug fix without merging the entire feature branch.
* A hotfix made in one branch needs to be applied to another branch.
* You accidentally committed to the wrong branch and want to move that commit.

---

# Command

## Cherry-pick a Commit

```bash id="h3k7wm"
git cherry-pick commitId
```

### Example

Suppose the commit hash is:

```text id="t8d9pz"
4f8c2ab
```

Run:

```bash id="p6r1xn"
git cherry-pick 4f8c2ab
```

Git copies that commit and applies it to your **current branch**.

---

# Example Workflow

Current branches:

```text id="8w2s1v"
main

A ─── B

feature-login

A ─── B ─── C ─── D
```

Commit C contains:

```text id="1r7bqe"
Fixed login validation
```

Switch to the main branch:

```bash id="x9l3ut"
git switch main
```

Copy only Commit C:

```bash id="v5n2mp"
git cherry-pick 4f8c2ab
```

Result:

```text id="j4m8kx"
main

A ─── B ─── C'

feature-login

A ─── B ─── C ─── D
```

The bug fix is now available in the `main` branch without bringing in Commit D.

---

# What Happens Internally?

When you run:

```bash id="d7y4qa"
git cherry-pick commitId
```

Git:

1. Finds the specified commit.
2. Copies its changes.
3. Applies those changes to the current branch.
4. Creates a **new commit** with a **new commit hash**.

The original commit remains unchanged in its original branch.

---

# Cherry-pick vs Merge

| Cherry-pick                        | Merge                                      |
| ---------------------------------- | ------------------------------------------ |
| Copies one specific commit.        | Combines all commits from another branch.  |
| Creates a new commit.              | Combines branch histories.                 |
| Useful for bug fixes and hotfixes. | Useful when an entire feature is complete. |
| Does not merge the whole branch.   | Merges the complete branch.                |

---

# Possible Cherry-pick Conflict

A cherry-pick can also produce a conflict if the same lines have been changed differently in the current branch.

Example:

```text id="y5z7cr"
Current Branch

console.log("Customer Login");
```

```text id="t3q8la"
Cherry-picked Commit

console.log("User Login");
```

Git may report a **Cherry-pick Conflict**.

Resolve it just like a merge conflict:

1. Edit the file.
2. Remove conflict markers.
3. Stage the file.
4. Continue the cherry-pick.

---

# Commands Summary

| Command                    | Purpose                                                             |
| -------------------------- | ------------------------------------------------------------------- |
| `git cherry-pick commitId` | Copies a specific commit from another branch to the current branch. |

---

# Best Practices

* Use cherry-pick only when you need a specific commit.
* Verify the commit hash before running the command.
* Resolve conflicts carefully if they occur.
* Prefer merging when you need the complete feature branch instead of individual commits.
* Avoid excessive cherry-picking, as it can create duplicate commits and make history harder to follow.

---

# Summary

| Term                     | Description                                                                     |
| ------------------------ | ------------------------------------------------------------------------------- |
| **Cherry-pick**          | Copies a specific commit from one branch to another.                            |
| **Commit ID**            | The unique hash that identifies the commit to copy.                             |
| **Cherry-picked Commit** | A new commit with the same changes as the original but a different commit hash. |

---

# Key Points

* `git cherry-pick` copies **one specific commit** into the current branch.
* It is commonly used to copy bug fixes or hotfixes without merging an entire branch.
* The copied commit receives a **new commit hash**.
* Cherry-pick may result in conflicts if the same code has been changed differently.
* Use cherry-pick when you need individual commits, and merge when you need the entire branch.
