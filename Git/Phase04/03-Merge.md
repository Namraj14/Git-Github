# 🔀 Git Merge

## What is Git Merge?

**Git Merge** is the process of combining changes from one branch into another.

It is commonly used to merge a **feature branch** into the **main branch** after the feature has been completed and tested.

Instead of copying files manually, Git intelligently combines the commit histories of both branches.

---

# Why Do We Need Merge?

Suppose you created a feature branch to develop a login page.

```text id="v2j8kq"
main
 │
 └── feature-login
```

You completed the login feature in `feature-login`.

Now you want those changes to become part of the main project.

This is done using **Git Merge**.

Without merging:

* The feature remains only in the feature branch.
* The `main` branch never receives the new changes.

---

# How Merge Works

Initially:

```text id="nxq3aj"
main
 │
 ├── Commit A
 └── Commit B

feature-login
 │
 ├── Commit A
 ├── Commit B
 └── Commit C (Login Feature)
```

After merging:

```text id="hzgx92"
main
 │
 ├── Commit A
 ├── Commit B
 └── Commit C (Login Feature)
```

Now the `main` branch contains the login feature.

---

# Steps to Merge a Feature Branch

### Step 1: Switch to the Main Branch

Before merging, move to the branch that should receive the changes.

```bash id="ylwq3g"
git switch main
```

---

### Step 2: Merge the Feature Branch

Run:

```bash id="8t1n4w"
git merge feature-login
```

Git copies the changes from `feature-login` into `main`.

---

# Merge Workflow

```text id="lw0m9k"
Create main
      │
      ▼
Create feature-login
      │
      ▼
Develop Login Feature
      │
      ▼
Switch to main
      │
      ▼
git merge feature-login
      │
      ▼
main now contains the login feature
```

---

# Example

Current branches:

```text id="jlwm61"
main
 │
 ├── Home Page
 └── Products

feature-login
 │
 ├── Login Page
 ├── Forgot Password
 └── Validation
```

Switch to the main branch:

```bash id="gwp0p5"
git switch main
```

Merge the feature:

```bash id="ktm48v"
git merge feature-login
```

Result:

```text id="j2uxqr"
main
 │
 ├── Home Page
 ├── Products
 ├── Login Page
 ├── Forgot Password
 └── Validation
```

The feature is now part of the main branch.

---

# Fast-Forward Merge

A **Fast-Forward Merge** happens when no new commits have been made on the `main` branch after creating the feature branch.

Example:

Before:

```text id="u6t0w9"
A ─── B (main)
       \
        C ─── D (feature-login)
```

After merge:

```text id="e4vjlwm"
A ─── B ─── C ─── D (main)
```

Git simply moves the `main` branch pointer forward.

---

# Merge Conflict (Introduction)

Sometimes Git cannot automatically merge changes.

This happens when:

* The same file was modified in both branches.
* The same lines were edited differently.

Example:

```text id="k1e67m"
main

login.js
↓

console.log("Login");
```

```text id="7dvr8v"
feature-login

login.js
↓

console.log("User Login");
```

Git doesn't know which version to keep.

This is called a **Merge Conflict**.

The conflict must be resolved manually before the merge can be completed.

---

# Commands Summary

| Command                   | Purpose                                                                       |
| ------------------------- | ----------------------------------------------------------------------------- |
| `git merge feature-login` | Merges the `feature-login` branch into the current branch (typically `main`). |

---

# Best Practices

* Always switch to the target branch (usually `main`) before merging.
* Test your feature branch before merging.
* Pull the latest changes from the remote repository before merging in a team environment.
* Resolve merge conflicts carefully if they occur.
* Delete feature branches after a successful merge to keep the repository clean.

---

# Summary

| Term               | Description                                                             |
| ------------------ | ----------------------------------------------------------------------- |
| **Merge**          | Combines changes from one branch into another.                          |
| **Feature Branch** | A branch used to develop a specific feature.                            |
| **Main Branch**    | The primary branch that receives completed and tested features.         |
| **Merge Conflict** | Occurs when Git cannot automatically combine changes from two branches. |

---

# Key Points

* `git merge` combines the changes from one branch into another.
* Merge is commonly used to bring completed feature branches into the `main` branch.
* Always switch to the destination branch before running `git merge`.
* Fast-forward merges occur when there are no new commits on the destination branch.
* Merge conflicts occur when the same part of a file has been changed in both branches and require manual resolution.
