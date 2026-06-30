# 📝 Git Reflog

## What is Git Reflog?

**Git Reflog** (Reference Log) is a log that records every movement of **HEAD** and branch references in your local repository.

Unlike `git log`, which shows only the commit history, `git reflog` shows **all the actions you've performed**, such as:

* Commits
* Checkouts
* Resets
* Rebases
* Merges
* Cherry-picks
* Branch switches

It acts like Git's **activity history**, making it possible to recover commits that may no longer appear in the normal commit history.

---

# Why Do We Need Git Reflog?

Sometimes you accidentally:

* Reset to a previous commit.
* Delete a branch.
* Perform a hard reset.
* Make a mistake during a rebase.

Normally, you might think the commit is lost.

However, Git Reflog remembers where **HEAD** was pointing, allowing you to recover those commits.

---

# Git Log vs Git Reflog

| Git Log                          | Git Reflog                                                                       |
| -------------------------------- | -------------------------------------------------------------------------------- |
| Shows commit history.            | Shows the history of HEAD and branch movements.                                  |
| Displays only reachable commits. | Displays all recent Git actions, including commits that are no longer reachable. |
| Used to review project history.  | Used to recover lost commits and undo mistakes.                                  |

---

# View Reflog

## Command

```bash
git reflog
```

### Purpose

Displays every recent action performed in the repository.

---

# Example Output

```text
a3b9f2d HEAD@{0}: commit: Added Login Page
f8c21d4 HEAD@{1}: checkout: moving from main to feature-login
c2e7a91 HEAD@{2}: reset: moving to HEAD~1
9d7b3e5 HEAD@{3}: commit: Fixed Login Bug
```

### Explanation

* `HEAD@{0}` → Current position of HEAD.
* `HEAD@{1}` → Previous action.
* `HEAD@{2}` → Action before that.
* `HEAD@{3}` → Older action.

---

# Understanding `HEAD@{}`

Git numbers every recorded action.

Example:

```text
HEAD@{0}
```

Current HEAD position.

```text
HEAD@{1}
```

Previous HEAD position.

```text
HEAD@{2}
```

Two actions ago.

These references can be used to return to an earlier state.

---

# Example Scenario

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

You accidentally run:

```bash
git reset --hard HEAD~1
```

Now:

```text
Commit A
   │
   ▼
Commit B ← HEAD
```

It looks like Commit C is gone.

Run:

```bash
git reflog
```

Output:

```text
abc1234 HEAD@{0}: reset: moving to HEAD~1
def5678 HEAD@{1}: commit: Added Feature C
```

The commit still exists in the reflog.

You can recover it using its commit hash or `HEAD@{1}`.

---

# Common Uses of Git Reflog

### Recover an accidentally deleted commit

After a hard reset or mistaken rebase.

---

### Recover a deleted branch

If the branch was recently checked out, reflog usually contains its last commit.

---

### Undo an incorrect reset

Find the previous HEAD position and restore it.

---

### Find previous branch positions

See exactly when and where you switched branches.

---

# Workflow

```text
Commit
    │
    ▼
Reset
    │
    ▼
Checkout
    │
    ▼
Rebase
    │
    ▼
Merge
    │
    ▼
All Actions Recorded
        │
        ▼
   git reflog
```

---

# Command Summary

| Command      | Purpose                                                                    |
| ------------ | -------------------------------------------------------------------------- |
| `git reflog` | Displays the history of HEAD and branch movements in the local repository. |

---

# Best Practices

* Use `git reflog` before assuming a commit is permanently lost.
* Check the reflog after an accidental `git reset --hard`.
* Use it to recover from mistakes during rebase or branch deletion.
* Remember that reflog is **local** to your repository and is not shared with remote repositories.

---

# Summary

| Term              | Description                                                          |
| ----------------- | -------------------------------------------------------------------- |
| **Reflog**        | A local history of HEAD and branch reference movements.              |
| **HEAD@{n}**      | Refers to a previous position of HEAD in the reflog.                 |
| **Recovery Tool** | Helps recover commits lost due to reset, rebase, or branch deletion. |

---

# Key Points

* `git reflog` records every movement of **HEAD** in your local repository.
* It is different from `git log` because it records Git operations, not just commit history.
* Reflog is one of the most useful tools for recovering accidentally lost commits.
* It can help recover work after a hard reset, rebase, or deleted branch.
* Reflog is stored **locally** and is not pushed to remote repositories like GitHub.
