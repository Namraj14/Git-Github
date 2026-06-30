# ⚠️ Merge Conflict

## What is a Merge Conflict?

A **Merge Conflict** occurs when Git is unable to automatically merge changes from two branches.

This usually happens when the **same part of the same file** has been modified differently in both branches.

Since Git cannot determine which version is correct, it asks you to resolve the conflict manually.

---

# Why Do Merge Conflicts Happen?

Merge conflicts typically occur when:

* Two developers modify the same line in a file.
* One developer deletes a file while another modifies it.
* The same file is renamed differently in two branches.
* Both branches contain incompatible changes.

---

# Example

Suppose the `main` branch contains:

```javascript
function login() {
    console.log("Login");
}
```

The `feature-login` branch changes it to:

```javascript
function login() {
    console.log("User Login");
}
```

Meanwhile, the `main` branch changes the same line to:

```javascript
function login() {
    console.log("Customer Login");
}
```

Now Git has two different versions of the same line and doesn't know which one to keep.

This results in a **Merge Conflict**.

---

# How Git Shows a Conflict

After attempting to merge:

```bash
git merge feature-login
```

Git may display:

```text
Auto-merging app.js
CONFLICT (content): Merge conflict in app.js
Automatic merge failed; fix conflicts and then commit the result.
```

Git also marks the conflicting file.

---

# Conflict Markers

Open the conflicted file, and you'll see something like:

```text
<<<<<<< HEAD
console.log("Customer Login");
=======
console.log("User Login");
>>>>>>> feature-login
```

### Meaning

* `<<<<<<< HEAD` → Code from the current branch (`main`).
* `=======` → Separator between the two versions.
* `>>>>>>> feature-login` → Code from the branch being merged.

These markers are added by Git and must be removed after resolving the conflict.

---

# How to Resolve a Merge Conflict

### Step 1: Open the Conflicted File

Locate the conflict markers.

---

### Step 2: Decide Which Code to Keep

You can:

* Keep the current branch's code.
* Keep the incoming branch's code.
* Combine both versions if appropriate.

Example (combined):

```javascript
function login() {
    console.log("Customer Login");
    console.log("User Login");
}
```

---

### Step 3: Remove Conflict Markers

Delete:

```text
<<<<<<< HEAD
=======
>>>>>>> feature-login
```

Only the final code should remain.

---

### Step 4: Stage the Resolved File

```bash
git add app.js
```

---

### Step 5: Complete the Merge

```bash
git commit
```

Git creates a merge commit, completing the merge process.

---

# Merge Conflict Workflow

```text
main
 │
 ├── Edit app.js
 │
feature-login
 │
 ├── Edit app.js
 │
 ▼
git merge feature-login
 │
 ▼
Merge Conflict
 │
 ▼
Resolve Conflict
 │
 ▼
git add app.js
 │
 ▼
git commit
```

---

# Example

Current branches:

```text
main
 │
 └── app.js → Customer Login

feature-login
 │
 └── app.js → User Login
```

Run:

```bash
git switch main
```

```bash
git merge feature-login
```

Git reports a conflict.

After resolving the file:

```bash
git add app.js
```

```bash
git commit
```

The merge is completed successfully.

---

# Practice Merge Conflicts

To become comfortable with conflict resolution, create and resolve at least **five manual merge conflicts**.

### Practice 1

Modify the same line in `app.js` on both branches.

---

### Practice 2

Modify the same line in `style.css` on both branches.

---

### Practice 3

Edit the same paragraph in `README.md` from both branches.

---

### Practice 4

Rename the same file differently in each branch and merge.

---

### Practice 5

Delete a file in one branch while modifying it in another branch.

---

# Commands Used

| Command                   | Purpose                                                |
| ------------------------- | ------------------------------------------------------ |
| `git merge feature-login` | Starts the merge process.                              |
| `git add app.js`          | Marks the conflict as resolved after editing the file. |
| `git commit`              | Completes the merge by creating a merge commit.        |

---

# Best Practices

* Pull the latest changes before starting new work.
* Keep feature branches short-lived to reduce conflicts.
* Commit small, focused changes frequently.
* Communicate with teammates when working on the same files.
* Read each conflict carefully before deciding which changes to keep.
* Never leave Git conflict markers in your final code.

---

# Summary

| Term                    | Description                                                                                                      |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------- |
| **Merge Conflict**      | A situation where Git cannot automatically combine changes from two branches.                                    |
| **Conflict Markers**    | Special markers (`<<<<<<<`, `=======`, `>>>>>>>`) added by Git to identify conflicting code.                     |
| **Conflict Resolution** | The process of editing the file, removing conflict markers, staging the resolved file, and completing the merge. |

---

# Key Points

* A merge conflict occurs when Git cannot automatically merge changes.
* Conflicts usually happen when the same lines of a file are changed in different branches.
* Git inserts conflict markers into the affected file.
* Resolve the conflict by choosing or combining the desired code, then remove the markers.
* Stage the resolved file with `git add` and finish the merge with `git commit`.
* Practicing manual conflict resolution is one of the best ways to build confidence with Git.
