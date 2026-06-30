# 🔀 Switch / Checkout

## What is Switching Branches?

**Switching branches** means moving from one branch to another so you can work on a different version of your project.

When you switch branches, Git updates your **Working Directory** to match the files and commits of the selected branch.

---

# Why Do We Switch Branches?

Suppose you have two branches:

* `main` → Stable production code
* `feature-login` → Login feature under development

Instead of mixing all your work in one branch, you can switch between them whenever needed.

This allows you to:

* Work on multiple features independently.
* Test different versions of your project.
* Keep the `main` branch stable.
* Resume work on any feature at any time.

---

# Example

Current branches:

```text id="3qp8he"
main
feature-login
feature-payment
```

You are currently on:

```text id="gxt17y"
* main
```

Now you want to continue developing the login feature.

Switch to:

```text id="ud1q6n"
feature-login
```

---

# Using `git switch`

## Command

```bash id="vjlwmj"
git switch feature-login
```

### Purpose

* Switches from the current branch to `feature-login`.
* Updates the Working Directory to match the selected branch.
* Does **not** create a new branch.

### Example

Current branch:

```text id="rjlwmc"
* main
```

Run:

```bash id="go2vjlwm"
git switch feature-login
```

Result:

```text id="h9j2bn"
* feature-login
```

Now all new commits will be added to `feature-login`.

---

# Using `git checkout`

Before Git introduced `git switch`, developers used `git checkout` to move between branches.

## Command

```bash id="l4yxt2"
git checkout feature-login
```

### Purpose

Switches to the `feature-login` branch.

### Example

Current branch:

```text id="sbgrmn"
* main
```

Run:

```bash id="6vbqpk"
git checkout feature-login
```

Result:

```text id="bcj6y8"
* feature-login
```

---

# Difference Between `git switch` and `git checkout`

| `git switch`                      | `git checkout`                                                                                              |
| --------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| Used only for switching branches. | Used for switching branches and several other operations (such as restoring files or checking out commits). |
| Easier for beginners.             | More powerful but can be confusing because it has multiple purposes.                                        |
| Introduced in Git 2.23.           | Available in older versions of Git.                                                                         |

For switching branches, **`git switch`** is the recommended command in modern Git.

---

# Example Workflow

Current repository:

```text id="crv63n"
main
 │
 └── feature-login
```

Current branch:

```text id="k13gzc"
* main
```

Switch to the login branch:

```bash id="8aepjm"
git switch feature-login
```

Now:

```text id="v9k0xk"
* feature-login
```

You continue developing the login feature.

Later, switch back to the main branch:

```bash id="6zjlwm"
git switch main
```

Now:

```text id="74uddu"
* main
```

You are again working on the stable version of the project.

---

# What Happens When You Switch Branches?

When you switch branches, Git:

* Moves **HEAD** to the selected branch.
* Updates the Working Directory.
* Loads the files from the selected branch.
* Future commits are added to the selected branch.

Example:

```text id="uml5hc"
Before

HEAD
 │
 ▼
main
```

After:

```bash id="jlwm4u"
git switch feature-login
```

```text id="jw3u9m"
HEAD
 │
 ▼
feature-login
```

---

# Commands Summary

| Command                      | Purpose                                                 |
| ---------------------------- | ------------------------------------------------------- |
| `git switch feature-login`   | Switches to the `feature-login` branch.                 |
| `git checkout feature-login` | Switches to the `feature-login` branch (older command). |

---

# Best Practices

* Use `git switch` when your goal is only to move between branches.
* Ensure your current work is committed or stashed before switching branches if you have conflicting changes.
* Verify your current branch using `git branch` before making new commits.
* Keep feature development on feature branches instead of the `main` branch.

---

# Summary

| Command                      | Description                                          |
| ---------------------------- | ---------------------------------------------------- |
| `git switch feature-login`   | Recommended command to switch to an existing branch. |
| `git checkout feature-login` | Older command used to switch branches.               |

---

# Key Points

* Switching branches allows you to work on different versions of your project.
* `git switch` is the modern and recommended command for changing branches.
* `git checkout` can also switch branches but has additional purposes beyond branch switching.
* Switching a branch moves **HEAD** to the selected branch and updates the Working Directory.
* New commits are always added to the branch you are currently on.
