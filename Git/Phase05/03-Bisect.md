# 🔎 Git Bisect

## What is Git Bisect?

**Git Bisect** is a debugging tool that helps you find **which commit introduced a bug**.

Instead of checking every commit one by one, Git uses a **binary search algorithm** to quickly identify the problematic commit.

This makes finding bugs much faster, especially in projects with hundreds or thousands of commits.

---

# Why Do We Need Git Bisect?

Imagine your project has **100 commits**.

Yesterday everything was working correctly.

Today, after several commits, a bug appears.

Without `git bisect`, you would have to manually check many commits.

With `git bisect`, Git automatically narrows down the search by repeatedly checking the middle commit.

---

# How Git Bisect Works

Suppose your commit history is:

```text id="zv8l1m"
A ─── B ─── C ─── D ─── E ─── F ─── G
```

Where:

* **Commit A** → Works correctly ✅
* **Commit G** → Contains a bug ❌

Git starts checking the middle commit.

```text id="epz5xr"
A ─── B ─── C ─── D ─── E ─── F ─── G
               ▲
          Test Commit D
```

If **D is good**, Git searches the second half.

If **D is bad**, Git searches the first half.

This continues until Git finds the exact commit that introduced the bug.

---

# What is Binary Search?

Binary Search works by dividing the search space into two halves every time.

Example:

```text id="3cqv8w"
100 Commits

↓

50

↓

25

↓

12

↓

6

↓

3

↓

1
```

Instead of checking all 100 commits, Git may only need about **7 checks**.

---

# Steps to Use Git Bisect

### Step 1: Start Bisect

```bash id="x2p4lm"
git bisect start
```

This tells Git to begin the bisect process.

---

### Step 2: Mark the Bad Commit

Usually, the current commit contains the bug.

```bash id="l7v5de"
git bisect bad
```

This marks the current commit as **bad**.

---

### Step 3: Mark a Good Commit

Choose an older commit where the project was working correctly.

```bash id="y9m8gt"
git bisect good <commit-hash>
```

Example:

```bash id="m3x7qa"
git bisect good 9fceb02
```

Git now checks out a commit between the good and bad commits.

---

### Step 4: Test the Project

Build and test your application.

If the checked-out commit works correctly:

```bash id="t6r4wn"
git bisect good
```

If it contains the bug:

```bash id="jlwm33"
git bisect bad
```

Git again selects the middle commit.

Repeat until Git identifies the first bad commit.

---

### Step 5: End the Bisect Session

After finding the problematic commit:

```bash id="jlwm34"
git bisect reset
```

This returns you to your original branch.

---

# Example Workflow

Commit history:

```text id="jlwm35"
A ─── B ─── C ─── D ─── E ─── F ─── G
```

* A → Good ✅
* G → Bad ❌

Start:

```bash id="jlwm36"
git bisect start
```

Mark bad:

```bash id="jlwm37"
git bisect bad
```

Mark good:

```bash id="jlwm38"
git bisect good A
```

Git checks out D.

If D is good:

```bash id="jlwm39"
git bisect good
```

Git checks F.

If F is bad:

```bash id="jlwm40"
git bisect bad
```

Git continues until it reports:

```text id="jlwm41"
E is the first bad commit
```

Reset:

```bash id="jlwm42"
git bisect reset
```

---

# Commands Summary

| Command                         | Purpose                                                     |
| ------------------------------- | ----------------------------------------------------------- |
| `git bisect start`              | Starts a bisect session.                                    |
| `git bisect bad`                | Marks the current commit as containing the bug.             |
| `git bisect good <commit-hash>` | Marks a known good commit.                                  |
| `git bisect good`               | Marks the currently checked-out commit as good.             |
| `git bisect reset`              | Ends the bisect session and returns to the original branch. |

---

# Best Practices

* Choose a commit that is definitely working as the **good** commit.
* Test each checked-out commit carefully before marking it as good or bad.
* Always run `git bisect reset` after finishing.
* Use `git bisect` when the bug was introduced over many commits—it's much faster than checking each commit manually.

---

# Summary

| Term              | Description                                                                                         |
| ----------------- | --------------------------------------------------------------------------------------------------- |
| **Git Bisect**    | A tool that finds the commit that introduced a bug using binary search.                             |
| **Good Commit**   | A commit where the application works correctly.                                                     |
| **Bad Commit**    | A commit where the bug exists.                                                                      |
| **Binary Search** | A search algorithm that repeatedly divides the search space in half to find the target efficiently. |

---

# Key Points

* `git bisect` helps identify the commit that introduced a bug.
* It uses **binary search**, making it much faster than manually checking every commit.
* You begin by marking one commit as **good** and another as **bad**.
* Git automatically checks out intermediate commits for testing.
* After identifying the first bad commit, use `git bisect reset` to return to your original branch.
