# 🌿 Git Branch

## What is a Branch?

A **branch** is an independent line of development in Git.

It allows you to work on new features, bug fixes, or experiments **without affecting the main project**.

Think of a branch as a copy of your project where you can safely make changes. Once the work is complete, it can be merged back into the main branch.

---

# Why Do Branches Exist?

Branches exist so that developers can work on different tasks simultaneously without interfering with each other's work.

Without branches:

* Everyone would work directly on the main code.
* Bugs and incomplete features could affect the stable project.
* Team collaboration would become difficult.
* Releasing stable software would be risky.

With branches:

* Developers can work independently.
* Multiple features can be developed at the same time.
* The main branch remains stable.
* Changes can be reviewed before merging.

---

# Main Branch

The **Main Branch** (commonly named `main`) is the primary branch of a Git repository.

It usually contains:

* Stable code
* Tested features
* Production-ready changes

Every repository starts with a main branch (or `master` in older repositories).

Example:

```text
main
 │
 ├── Initial Project
 ├── Login Module
 ├── Dashboard
 └── Payment Module
```

The `main` branch should always contain code that is ready to use.

---

# Feature Branch

A **Feature Branch** is created from the main branch to develop a specific feature or fix.

Examples:

* `feature-login`
* `feature-payment`
* `feature-dashboard`
* `feature-search`

Instead of changing the `main` branch directly, developers create feature branches.

Example:

```text
                feature-login
                     │
                     ▼
main ────────────────●────────────
```

When the feature is completed and tested, it is merged back into `main`.

---

# Why Use a Feature Branch?

Suppose you're developing a login page.

Instead of writing code directly in `main`, create a new branch:

```text
main
 │
 ├── Stable Project
 │
 └──────────────► feature-login
                     │
                     ├── Add Login Page
                     ├── Add Validation
                     └── Fix Bugs
```

If something goes wrong, only the feature branch is affected.

The `main` branch remains safe.

---

# Branch Workflow

```text
               main
                 │
                 ▼
         Create Branch
                 │
                 ▼
         feature-login
                 │
          Develop Feature
                 │
                 ▼
          Merge into main
```

---

# View All Branches

Use:

```bash
git branch
```

### Purpose

Displays all local branches.

### Example Output

```text
* main
  feature-login
  feature-payment
```

The `*` indicates the branch you are currently working on.

---

# Create a New Branch

Use:

```bash
git branch feature-login
```

### Purpose

Creates a new branch named `feature-login`.

> **Note:** This command **only creates** the branch. It does **not** switch you to it.

Example:

Current branch:

```text
main
```

Run:

```bash
git branch feature-login
```

Now the repository has two branches:

```text
main
feature-login
```

You are still on the `main` branch until you explicitly switch to the new branch.

---

# Example

Suppose your project currently has:

```text
main
 │
 ├── Home Page
 ├── Products
 └── Cart
```

You need to build a login page.

Instead of modifying `main`, create a feature branch:

```bash
git branch feature-login
```

Now:

```text
main
 │
 └────────────► feature-login
                   │
                   ├── Login Page
                   ├── Forgot Password
                   └── Validation
```

The login feature is developed independently without affecting the stable project.

---

# Commands Summary

| Command                    | Purpose                                     |
| -------------------------- | ------------------------------------------- |
| `git branch`               | Displays all local branches.                |
| `git branch feature-login` | Creates a new branch named `feature-login`. |

---

# Best Practices

* Keep the `main` branch stable and production-ready.
* Create a separate feature branch for each new feature or bug fix.
* Give branches meaningful names such as `feature-login`, `bugfix-payment`, or `feature-dashboard`.
* Delete feature branches after they have been merged to keep the repository clean.

---

# Summary

| Term               | Description                                                                              |
| ------------------ | ---------------------------------------------------------------------------------------- |
| **Branch**         | An independent line of development in Git.                                               |
| **Main Branch**    | The primary branch that contains stable, production-ready code.                          |
| **Feature Branch** | A branch created to develop a specific feature or fix without affecting the main branch. |

---

# Key Points

* A branch allows you to develop features independently.
* The **main** branch should contain stable code.
* A **feature branch** is used for developing a single feature or fixing a specific issue.
* `git branch` lists all local branches.
* `git branch feature-login` creates a new branch but does not switch to it.
* Branches make collaboration safer and keep the main project stable.
