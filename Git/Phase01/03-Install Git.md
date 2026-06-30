# 💻 Install Git

## What is Git Installation?

Before using Git, you must install it on your computer. Installing Git adds the Git software and command-line tools, allowing you to track changes, create repositories, and use Git commands.

---

# 1. Install Git

### Windows

1. Go to the official Git website:
   **https://git-scm.com**
2. Download the latest version for Windows.
3. Run the installer.
4. Keep the default settings (recommended for beginners).
5. Click **Next** until the installation is complete.
6. Click **Finish**.

---

### macOS

Using Homebrew:

```bash
brew install git
```

Or download the installer from:

**https://git-scm.com**

---

### Linux (Ubuntu/Debian)

```bash
sudo apt update
sudo apt install git
```

---

# 2. Verify Git Installation

After installing Git, open **Command Prompt**, **PowerShell**, or **Terminal** and run:

```bash
git --version
```

### Example Output

```text
git version 2.51.0
```

### Purpose

* Checks whether Git is installed correctly.
* Displays the installed Git version.

If you see a version number, Git has been installed successfully.

---

# 3. Configure Username

Git records the author's name with every commit.

Use the following command:

```bash
git config --global user.name "Your Name"
```

### Example

```bash
git config --global user.name "John Doe"
```

### Purpose

* Sets your name for all Git repositories on your computer.
* Every commit you make will be associated with this name.

---

# 4. Configure Email

Git also records the author's email address with every commit.

Use:

```bash
git config --global user.email "your@email.com"
```

### Example

```bash
git config --global user.email "john@example.com"
```

### Purpose

* Associates your email with every commit.
* If you're using GitHub, it's recommended to use the same email linked to your GitHub account.

---

# 5. View Git Configuration

To display all configured Git settings, run:

```bash
git config --list
```

### Example Output

```text
user.name=John Doe
user.email=john@example.com
core.editor=vim
core.autocrlf=true
```

### Purpose

Displays all Git configuration values, including:

* Username
* Email
* Default editor
* Line-ending settings
* Other Git configurations

---

# Commands Summary

| Command                                           | Purpose                                                   |
| ------------------------------------------------- | --------------------------------------------------------- |
| `git --version`                                   | Displays the installed Git version.                       |
| `git config --global user.name "Your Name"`       | Sets your username for all repositories on your computer. |
| `git config --global user.email "your@email.com"` | Sets your email for all repositories on your computer.    |
| `git config --list`                               | Displays all current Git configuration settings.          |

---

# Key Points

* Install Git before using any Git commands.
* Verify the installation using `git --version`.
* Configure your username and email before making your first commit.
* Use the `--global` option to apply these settings to all repositories on your computer.
* Use `git config --list` to verify your configuration.
