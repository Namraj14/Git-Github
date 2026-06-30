# 📚 What is Version Control?

## What is Version Control?

**Version Control** is a system that records and manages changes made to files over time. It allows you to save different versions of your project, track modifications, and restore previous versions whenever needed.

Instead of overwriting the same file repeatedly, version control keeps a history of every change.

### Example

Without version control:

```text
Project/
├── Resume_Final.docx
├── Resume_Final_New.docx
├── Resume_Final_Latest.docx
├── Resume_Final_Updated.docx
```

It becomes difficult to know which file is the latest.

With version control:

```text
Project
│
├── Version 1
├── Version 2
├── Version 3
└── Version 4
```

Each version is recorded with information such as:

* What changed
* Who made the change
* When it was made
* Why it was made (through a commit message)

---

# Why Git Was Created?

Before Git, developers mainly used centralized version control systems such as CVS and SVN.

These systems had several limitations:

* Required a constant connection to a central server.
* Slow performance for large projects.
* If the central server failed, development could be interrupted.
* Branching and merging were slow and difficult.
* Developers couldn't work efficiently offline.

To solve these problems, **Git** was created by **Linus Torvalds** in **2005** for the development of the Linux kernel.

Git introduced a **distributed version control system**, where every developer has a complete copy of the repository, making development faster, safer, and more reliable.

---

# Problems Without Git

Without Git, developers may face several challenges:

### 1. No History of Changes

You cannot easily see what was changed or when it was changed.

---

### 2. No Backup of Previous Versions

If a file is accidentally deleted or modified, recovering an older version is difficult.

---

### 3. Collaboration Becomes Difficult

When multiple developers work on the same project, their changes can overwrite each other.

---

### 4. No Easy Rollback

If a new change introduces bugs, there is no simple way to return to a working version.

---

### 5. File Duplication

Developers often create multiple copies of the same file:

```text
Project_v1
Project_v2
Project_Final
Project_Final_New
Project_Final_Latest
```

This creates confusion and wastes storage.

---

### 6. No Record of Who Changed What

Without version control, it's difficult to identify:

* Who made a change
* What was changed
* Why it was changed

---

# Git vs GitHub

| Git                                            | GitHub                                                                       |
| ---------------------------------------------- | ---------------------------------------------------------------------------- |
| A distributed version control system           | A cloud-based platform for hosting Git repositories                          |
| Installed on your computer                     | Accessed through a web browser or Git client                                 |
| Tracks changes in your project                 | Stores and shares Git repositories online                                    |
| Works offline                                  | Internet is typically required for synchronization                           |
| Manages commits, branches, and version history | Provides collaboration features like pull requests, issues, and code reviews |

### Simple Analogy

* **Git** is like **Microsoft Word** on your computer, where you create and edit documents.
* **GitHub** is like **Google Drive**, where you store, share, and collaborate on those documents online.

Git can be used without GitHub, but GitHub relies on Git to manage version history.

---

# Key Points

* **Version Control** is a system that tracks changes to files over time.
* **Git** is a distributed version control system created to overcome the limitations of older centralized systems.
* Without Git, managing versions, collaboration, and recovery becomes difficult.
* **Git** is the tool that manages version history, while **GitHub** is a platform that hosts Git repositories and enables collaboration.
