# 📦 Git Squash

## What is Git Squash?

**Git Squash** is the process of **combining multiple commits into a single commit**.

Instead of having many small commits, Git creates **one clean, meaningful commit**.

Squashing is commonly done using **Interactive Rebase** before merging a feature branch.

---

# Why Do We Need Squash?

While developing a feature, you might create many small commits:

```text id="w9f6px"
Commit 1 → Created Login Page
Commit 2 → Fixed CSS
Commit 3 → Fixed Validation
Commit 4 → Fixed Typo
Commit 5 → Updated Button
```

These commits are useful during development, but they make the Git history cluttered.

Instead, you can squash them into one commit:

```text id="gmr2qh"
Commit 1 → Added Login Feature
```

Now the project history is much cleaner.

---

# Benefits of Squashing

* Cleaner commit history.
* Easier code reviews.
* One meaningful commit per feature.
* Removes unnecessary "fix" commits.
* Makes project history easier to understand.

---

# How Squash Works

### Before Squash

```text id="5kpw8c"
A ─── B ─── C ─── D ─── E
```

Where:

* B → Created Login Page
* C → Fixed CSS
* D → Fixed Validation
* E → Updated Button

---

### After Squash

```text id="q7a2mv"
A ─── F
```

Commit **F** contains all the changes from B, C, D, and E.

The old commits are replaced with one new commit.

---

# Squashing Using Interactive Rebase

## Command

```bash id="a9n6qx"
git rebase -i HEAD~3
```

### Purpose

Starts an **Interactive Rebase** for the last three commits.

Git opens an editor:

```text id="jlwm51"
pick a1b2c3 Added Login Page
pick d4e5f6 Fixed Validation
pick g7h8i9 Updated CSS
```

Change it to:

```text id="jlwm52"
pick a1b2c3 Added Login Page
squash d4e5f6 Fixed Validation
squash g7h8i9 Updated CSS
```

Save and close the editor.

Git combines all three commits into one.

---

# Example Workflow

Current history:

```text id="jlwm53"
Commit A
   │
   ▼
Commit B → Added Login Page
   │
   ▼
Commit C → Fixed Validation
   │
   ▼
Commit D → Updated CSS
```

Run:

```bash id="jlwm54"
git rebase -i HEAD~3
```

Choose:

```text id="jlwm55"
pick Commit B
squash Commit C
squash Commit D
```

Result:

```text id="jlwm56"
Commit A
   │
   ▼
Commit E → Added Login Feature
```

The three commits are now a single commit.

---

# Squash vs Merge

| Squash                                   | Merge                             |
| ---------------------------------------- | --------------------------------- |
| Combines multiple commits into one.      | Combines two branches.            |
| Produces a cleaner history.              | Preserves all individual commits. |
| Used before merging or cleaning history. | Used to integrate branches.       |

---

# Squash vs Cherry-pick

| Squash                             | Cherry-pick                                   |
| ---------------------------------- | --------------------------------------------- |
| Combines several commits into one. | Copies one specific commit to another branch. |
| Used to simplify history.          | Used to transfer selected changes.            |

---

# When Should You Squash?

Use squash when:

* A feature has many small "work in progress" commits.
* You want one clean commit for a pull request.
* You want to remove unnecessary fix-up commits.
* You are cleaning your local branch before sharing it.

---

# Important Note

Squashing **rewrites commit history**.

Therefore:

* ✅ Safe on your own local feature branch.
* ❌ Avoid squashing commits that have already been pushed and shared with other developers unless your team agrees.

---

# Commands Summary

| Command                | Purpose                                                                                           |
| ---------------------- | ------------------------------------------------------------------------------------------------- |
| `git rebase -i HEAD~3` | Opens Interactive Rebase for the last three commits, allowing you to squash them into one commit. |

---

# Best Practices

* Squash multiple small commits into one meaningful commit before merging a feature branch.
* Write a clear commit message after squashing.
* Keep one logical feature per commit.
* Avoid squashing commits that have already been shared with others.

---

# Summary

| Term                   | Description                                                                  |
| ---------------------- | ---------------------------------------------------------------------------- |
| **Squash**             | Combines multiple commits into a single commit.                              |
| **Interactive Rebase** | A Git feature used to edit, reorder, rename, or squash commits.              |
| **Clean History**      | A concise commit history with meaningful commits instead of many small ones. |

---

# Key Points

* Git Squash combines multiple commits into one.
* Squashing is commonly performed using **Interactive Rebase**.
* It creates a cleaner and more readable Git history.
* Use squash before merging a feature branch to keep the repository organized.
* Since squashing rewrites commit history, use it carefully on shared branches.
