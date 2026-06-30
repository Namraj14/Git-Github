# 🏷️ Git Tags

## What is a Git Tag?

A **Git Tag** is a permanent label attached to a specific commit.

Tags are commonly used to **mark important versions** of a project, such as software releases.

Unlike branches, tags do **not move**. Once a tag is created, it always points to the same commit.

---

# Why Do We Need Tags?

Suppose you're developing an application.

Your commit history looks like this:

```text
Commit A → Initial Project
Commit B → Added Login
Commit C → Added Dashboard
Commit D → Fixed Bugs
Commit E → Payment Module
```

After testing, you release **Version 1.0**.

Instead of remembering the commit hash, you can create a tag:

```text
v1.0
 │
 ▼
Commit D
```

Later, when Version 2.0 is released:

```text
v1.0
 │
 ▼
Commit D

v2.0
 │
 ▼
Commit E
```

Now you can easily identify different releases.

---

# Why Use Tags?

Tags help you:

* Mark software releases.
* Identify stable versions.
* Return to a specific version easily.
* Share release versions with your team.
* Maintain version history.

---

# Branch vs Tag

| Branch                                | Tag                                      |
| ------------------------------------- | ---------------------------------------- |
| Moves whenever new commits are added. | Always points to the same commit.        |
| Used for ongoing development.         | Used for marking releases or milestones. |
| Can receive new commits.              | Cannot receive new commits.              |

---

# View All Tags

## Command

```bash
git tag
```

### Purpose

Displays all tags in the repository.

### Example Output

```text
v1.0
v1.1
v2.0
```

---

# Create a Tag

## Command

```bash
git tag v1.0
```

### Purpose

Creates a tag named `v1.0` on the current commit (`HEAD`).

### Example

Current history:

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
git tag v1.0
```

Result:

```text
Commit A
   │
   ▼
Commit B
   │
   ▼
Commit C ← HEAD
     ▲
     │
    v1.0
```

The tag now permanently points to Commit C.

---

# Push a Tag to Remote Repository

Creating a tag locally does **not** automatically send it to GitHub.

To push a tag:

```bash
git push origin v1.0
```

### Purpose

Uploads the `v1.0` tag to the remote repository.

After this, other developers can see and use the tag.

---

# Example Workflow

Current history:

```text
Commit A
   │
   ▼
Commit B
   │
   ▼
Commit C ← HEAD
```

Create a release:

```bash
git tag v1.0
```

Check the tag:

```bash
git tag
```

Output:

```text
v1.0
```

Push the tag:

```bash
git push origin v1.0
```

Now the tag is available in the remote repository.

---

# Common Version Naming

Developers commonly follow **Semantic Versioning (SemVer)**.

Examples:

```text
v1.0.0
v1.1.0
v1.2.3
v2.0.0
```

Meaning:

* **Major Version** → Breaking changes.
* **Minor Version** → New features without breaking existing functionality.
* **Patch Version** → Bug fixes and small improvements.

Example:

| Version  | Meaning                             |
| -------- | ----------------------------------- |
| `v1.0.0` | First stable release                |
| `v1.1.0` | New features added                  |
| `v1.1.1` | Bug fixes                           |
| `v2.0.0` | Major release with breaking changes |

---

# Commands Summary

| Command                | Purpose                                           |
| ---------------------- | ------------------------------------------------- |
| `git tag`              | Displays all tags in the repository.              |
| `git tag v1.0`         | Creates a tag named `v1.0` on the current commit. |
| `git push origin v1.0` | Pushes the `v1.0` tag to the remote repository.   |

---

# Best Practices

* Create tags only for important releases or milestones.
* Use meaningful version names such as `v1.0.0` or `v2.1.0`.
* Push tags to the remote repository after creating them.
* Do not use tags for ongoing development—use branches instead.
* Follow Semantic Versioning for consistent release management.

---

# Summary

| Term            | Description                                                     |
| --------------- | --------------------------------------------------------------- |
| **Tag**         | A permanent label pointing to a specific commit.                |
| **Versioning**  | The practice of assigning version numbers to software releases. |
| **Release Tag** | A tag used to identify a released version of the project.       |

---

# Key Points

* A Git tag is a permanent reference to a specific commit.
* Tags are primarily used for software versioning and releases.
* Unlike branches, tags do not move when new commits are added.
* `git tag` lists all existing tags.
* `git tag v1.0` creates a new tag on the current commit.
* `git push origin v1.0` uploads the tag to the remote repository so others can access it.
