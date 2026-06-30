# 🚫 Git Ignore (`.gitignore`)

## What is `.gitignore`?

A **`.gitignore`** file tells Git **which files and folders should not be tracked**.

Any file or folder listed in `.gitignore` will be ignored by Git, meaning it won't appear in `git status` and won't be included in commits.

The `.gitignore` file is placed in the root directory of your Git repository.

---

# Why Do We Need `.gitignore`?

Not every file in a project should be stored in Git.

Some files are:

* Automatically generated.
* Temporary.
* Very large.
* Contain sensitive information.
* Specific to a developer's local machine.

Ignoring these files keeps the repository:

* Clean
* Secure
* Smaller
* Easier to collaborate on

---

# Common Files to Ignore

## 1. `node_modules/`

```text id="ghp7d2"
node_modules/
```

### What is it?

The `node_modules` folder contains all the packages installed by **Node.js**.

Example:

```text id="q8x4ye"
Project/
│
├── node_modules/
├── package.json
└── app.js
```

### Why Ignore It?

* Can contain thousands of files.
* Very large in size.
* Can be recreated anytime using:

```bash id="jlwm12"
npm install
```

---

## 2. `.env`

```text id="v2c5jr"
.env
```

### What is it?

The `.env` file stores **environment variables**.

Example:

```text id="jlwm13"
DB_PASSWORD=mySecretPassword
API_KEY=abcd1234
JWT_SECRET=xyz789
```

### Why Ignore It?

It often contains sensitive information such as:

* Database passwords
* API keys
* Secret tokens
* Authentication credentials

These should never be pushed to GitHub.

---

## 3. `*.log`

```text id="jlwm14"
*.log
```

### What Does `*` Mean?

The `*` is a wildcard that matches any file name.

Example:

```text id="jlwm15"
error.log
server.log
debug.log
application.log
```

All files ending with `.log` will be ignored.

### Why Ignore Them?

Log files:

* Are automatically generated.
* Change frequently.
* Are usually not required by other developers.

---

# Example `.gitignore` File

```text id="jlwm16"
node_modules/
.env
*.log
```

This tells Git to ignore:

* The entire `node_modules` folder.
* The `.env` file.
* Every file ending with `.log`.

---

# How `.gitignore` Works

Suppose your project contains:

```text id="jlwm17"
Project/
│
├── app.js
├── package.json
├── node_modules/
├── .env
├── error.log
└── README.md
```

`.gitignore`

```text id="jlwm18"
node_modules/
.env
*.log
```

Running:

```bash id="jlwm19"
git status
```

Output:

```text id="jlwm20"
Untracked files:

app.js
package.json
README.md
```

Git ignores:

* `node_modules/`
* `.env`
* `error.log`

---

# Important Note

`.gitignore` only affects **untracked files**.

If a file has already been committed, adding it to `.gitignore` **does not stop Git from tracking it**.

Example:

1. Commit `.env`

```bash id="jlwm21"
git add .env
git commit -m "Added env file"
```

2. Later add:

```text id="jlwm22"
.env
```

to `.gitignore`.

Git will **still track** `.env`.

To stop tracking it, remove it from Git's index:

```bash id="jlwm23"
git rm --cached .env
```

Then commit the change.

---

# Common `.gitignore` Entries

```text id="jlwm24"
node_modules/
.env
*.log
dist/
build/
coverage/
.vscode/
.idea/
```

---

# Commands Used

Although `.gitignore` itself is just a file, you'll commonly use:

```bash id="jlwm25"
git status
```

to verify that ignored files no longer appear in Git's output.

---

# Best Practices

* Create a `.gitignore` file when starting a new project.
* Never commit sensitive files like `.env`.
* Ignore generated folders such as `node_modules` and `build`.
* Ignore log files and temporary files.
* Review your `git status` before committing to ensure unnecessary files are not included.

---

# Summary

| Entry           | Purpose                                                |
| --------------- | ------------------------------------------------------ |
| `node_modules/` | Ignores the Node.js dependency folder.                 |
| `.env`          | Ignores environment variable files containing secrets. |
| `*.log`         | Ignores all log files.                                 |

---

# Key Points

* `.gitignore` tells Git which files and folders should not be tracked.
* Ignored files do not appear in `git status` if they are untracked.
* `node_modules/` is ignored because it is large and can be regenerated.
* `.env` is ignored because it often contains sensitive information.
* `*.log` ignores every log file using a wildcard pattern.
* `.gitignore` does **not** affect files that are already being tracked; those must first be removed from Git's index using `git rm --cached`.
