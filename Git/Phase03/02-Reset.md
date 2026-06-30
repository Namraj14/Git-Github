# 🔄 Git Reset

## What is Git Reset?

The **`git reset`** command is used to **move the current branch (HEAD) to a previous commit**.

Depending on the option used, Git can:

* Remove commits.
* Keep or remove staged changes.
* Keep or remove changes in the Working Directory.

> **Important:** `git reset` is mainly used to undo **local commits**. Avoid using it on commits that have already been pushed to a shared remote repository, as it rewrites history.

---

# Understanding HEAD~1

Before learning reset types, understand this notation:

```text
HEAD
```

Represents the **current (latest) commit**.

```text
HEAD~1
```

Represents **one commit before HEAD**.

Example:

```text id="u4j9a2"
Commit A
   │
   ▼
Commit B
   │
   ▼
Commit C ← HEAD
```

Here:

* `HEAD` → Commit C
* `HEAD~1` → Commit B

If you reset to `HEAD~1`, Git moves HEAD from **Commit C** back to **Commit B**.

---

# Git Areas

To understand reset, remember the three Git areas:

```text id="e34mpv"
Working Directory
        │
        ▼
Staging Area
        │
        ▼
Local Repository (HEAD)
```

Each reset type affects these areas differently.

---

# 1. Soft Reset

## Command

```bash id="v5j0ut"
git reset --soft HEAD~1
```

## What Does It Do?

A **Soft Reset**:

* Moves HEAD to the previous commit.
* Removes the last commit from history.
* Keeps all changes in the **Staging Area**.
* Does **not** modify the Working Directory.

### Before

```text id="zh0wko"
Working Directory ✔
Staging Area ✔
Commit C ← HEAD
```

### After

```text id="fsw5td"
Working Directory ✔
Staging Area ✔
Commit B ← HEAD
```

The changes from Commit C are still staged and ready to be committed again.

### When to Use

Use a soft reset when:

* You want to change the last commit message.
* You forgot to include a file in the last commit.
* You want to recreate the last commit.

---

# 2. Mixed Reset

## Command

```bash id="l7qgye"
git reset --mixed HEAD~1
```

> `--mixed` is the **default** reset mode. Running `git reset HEAD~1` has the same effect.

## What Does It Do?

A **Mixed Reset**:

* Moves HEAD to the previous commit.
* Removes the last commit.
* Clears the Staging Area.
* Keeps all changes in the Working Directory.

### Before

```text id="ecm0b6"
Working Directory ✔
Staging Area ✔
Commit C ← HEAD
```

### After

```text id="rzh1bk"
Working Directory ✔
Staging Area ❌
Commit B ← HEAD
```

The files become **modified** and must be staged again before committing.

### When to Use

Use a mixed reset when:

* You committed too early.
* You want to review your changes before staging them again.
* You want to reorganize your next commit.

---

# 3. Hard Reset

## Command

```bash id="y5zsl8"
git reset --hard HEAD~1
```

## What Does It Do?

A **Hard Reset**:

* Moves HEAD to the previous commit.
* Removes the last commit.
* Clears the Staging Area.
* Deletes all changes in the Working Directory.

### Before

```text id="0q8e8q"
Working Directory ✔
Staging Area ✔
Commit C ← HEAD
```

### After

```text id="70e1po"
Working Directory ❌
Staging Area ❌
Commit B ← HEAD
```

Everything from Commit C and any uncommitted changes are discarded.

> **Warning:** Changes removed by `git reset --hard` are usually difficult or impossible to recover if they were never committed elsewhere.

### When to Use

Use a hard reset when:

* You want to completely discard local changes.
* You want your repository to exactly match an earlier commit.
* You are certain you no longer need the discarded work.

---

# Comparison

| Reset Type | HEAD       | Staging Area     | Working Directory |
| ---------- | ---------- | ---------------- | ----------------- |
| **Soft**   | Moves back | ✅ Keeps changes  | ✅ Keeps changes   |
| **Mixed**  | Moves back | ❌ Clears staging | ✅ Keeps changes   |
| **Hard**   | Moves back | ❌ Clears staging | ❌ Deletes changes |

---

# Example Workflow

Current history:

```text id="ot7qqv"
Commit A
   │
   ▼
Commit B
   │
   ▼
Commit C ← HEAD
```

### Soft Reset

```bash id="2kr5gf"
git reset --soft HEAD~1
```

Result:

* HEAD → Commit B
* Commit C removed
* Changes from Commit C remain staged.

---

### Mixed Reset

```bash id="s7wtb6"
git reset --mixed HEAD~1
```

Result:

* HEAD → Commit B
* Commit C removed
* Changes become modified in the Working Directory.

---

### Hard Reset

```bash id="ej6e0t"
git reset --hard HEAD~1
```

Result:

* HEAD → Commit B
* Commit C removed
* Staging Area cleared
* Working Directory restored to Commit B.

---

# Commands Summary

| Command                    | Purpose                                                                                 |
| -------------------------- | --------------------------------------------------------------------------------------- |
| `git reset --soft HEAD~1`  | Removes the last commit but keeps all changes staged.                                   |
| `git reset --mixed HEAD~1` | Removes the last commit, unstages the changes, and keeps them in the Working Directory. |
| `git reset --hard HEAD~1`  | Removes the last commit and permanently discards staged and working directory changes.  |

---

# Best Practices

* Use **Soft Reset** when you only want to modify or recreate the last commit.
* Use **Mixed Reset** when you want to keep your work but stage it again later.
* Use **Hard Reset** only when you are absolutely sure you want to discard your changes.
* Avoid using `git reset` on commits that have already been pushed to a shared remote repository.

---

# Summary

| Reset Type      | Commit Removed | Staged Changes | Working Directory Changes |
| --------------- | -------------- | -------------- | ------------------------- |
| **Soft Reset**  | ✅ Yes          | ✅ Kept         | ✅ Kept                    |
| **Mixed Reset** | ✅ Yes          | ❌ Removed      | ✅ Kept                    |
| **Hard Reset**  | ✅ Yes          | ❌ Removed      | ❌ Removed                 |

---

# Key Points

* `git reset` moves **HEAD** to an earlier commit.
* **Soft Reset** keeps your changes staged.
* **Mixed Reset** keeps your changes but unstages them.
* **Hard Reset** removes the commit and deletes local changes.
* Choose the reset type based on whether you want to keep or discard your staged and working directory changes.
