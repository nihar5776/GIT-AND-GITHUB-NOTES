# Module 2: Setup & Initialization

---

## 2.1 Installing Git

### Windows

1. Open your browser and go to [git-scm.com](https://git-scm.com)
2. Click **Download** → Choose **Windows**
3. Select either **32-bit** or **64-bit** based on your system
4. Run the installer and follow the prompts (defaults are fine)

### macOS

**Option 1 — Homebrew (Recommended):**
```bash
brew install git
```

**Option 2 — Installer:**
1. Go to [git-scm.com](https://git-scm.com) → Download → macOS
2. Follow the installation instructions

### Linux (Ubuntu/Debian)

```bash
sudo apt update
sudo apt install git
```

### Linux (Fedora/RHEL)

```bash
sudo dnf install git
```

---

## 2.2 Terminal Setup

After installing Git, you need a terminal to run commands.

| OS | Terminal Options |
|----|-----------------|
| **Windows** | Command Prompt, PowerShell, or **Git Bash** (recommended) |
| **macOS** | Terminal app (built-in) |
| **Linux** | Any terminal emulator |

> **Tip:** Many developers prefer **Git Bash** on Windows because it feels similar to a Linux terminal and makes running Git commands easier and more intuitive.

---

## 2.3 Verifying Installation

Open your terminal and type:

```bash
git --version
```

**Expected output:**
```
git version 2.45.1
```

> The version number may differ depending on when you installed Git. If you see a version number, Git is installed correctly. If you get an error, Git is not installed — go back and install it.

---

## 2.4 Essential Terminal Commands (Non-Git)

These are **general terminal commands** — not Git commands — but you'll use them all the time:

| Command | Description | Example |
|---------|-------------|---------|
| `cd <folder>` | Change directory (move into a folder) | `cd Desktop` |
| `cd ..` | Move one level up | `cd ..` |
| `pwd` | Print working directory (show current path) | `pwd` |
| `ls` | List files and folders | `ls` |
| `ls -la` | List **all** files (including hidden ones) | `ls -la` |
| `mkdir <name>` | Create a new directory | `mkdir my-project` |
| `touch <name>` | Create a new empty file | `touch index.html` |
| `rm <file>` | Delete a file | `rm old.txt` |
| `rm -r <folder>` | Delete a folder recursively | `rm -r my-folder` |

> **Windows Note:** Some commands differ on Windows CMD. For example, use `dir` instead of `ls`, and `type nul >` instead of `touch`. **Git Bash** on Windows supports all the Linux-style commands above.

---

## 2.5 Creating a Local Project

### Step-by-Step Initial Setup Example:

| Step | Command | Directory State | File Status (Git Context) | Description & Internal Action |
|------|---------|-----------------|---------------------------|--------------------------------|
| **1** | `cd Desktop` | `/Desktop` | **Untracked** | Moves the terminal focus to the user's Desktop directory. |
| **2** | `mkdir git-1` | `/Desktop/git-1` | **Untracked** | Creates a new normal OS directory named `git-1`. |
| **3** | `cd git-1` | `/Desktop/git-1` | **Untracked** | Enters the new project folder. |
| **4** | `touch 1.txt 2.txt` | `/Desktop/git-1` | **Untracked** | Creates two empty text files `1.txt` and `2.txt` in the root. |
| **5** | `mkdir my-folder`<br>`touch my-folder/3.txt` | `/Desktop/git-1/my-folder` | **Untracked** | Creates a subfolder `my-folder` containing `3.txt`. |

**Result — your local folder structure:**
```
git-1/
├── 1.txt
├── 2.txt
└── my-folder/
    └── 3.txt
```

---

## 2.6 `git init` — Initializing a Repository

Once you have a project folder, you need to tell Git: **"Start tracking this folder."**

### Command:
```bash
git init
```

### Command Output:
```
Initialized empty Git repository in /Users/you/Desktop/git-1/.git/
```

### Detailed Step-by-Step Status & Internals:

| Action / Check | Command | System Status | Git Internal Functionality |
|---|---|---|---|
| **Initialize Repo** | `git init` | Directory is now a **local Git repository** | Creates the hidden `.git/` folder containing standard metadata config files. |
| **Check Hidden Files** | `ls -la` | Displays files plus the hidden `.git` folder | Shows that Git has successfully mounted itself in this directory. |
| **Check Project Status** | `git status` | Lists all files as **Untracked** | Git scans the workspace and detects `1.txt`, `2.txt`, and `my-folder/` but isn't watching changes yet. |

### Inside the hidden `.git` folder:
When you run `git init`, Git initializes several key files and directories:

- 📂 `objects/` — The database where Git stores all compressed code blobs, trees, and commit metadata.
- 📂 `refs/` — Stores pointers to branches and tags (e.g., `refs/heads/main`).
- 📄 `config` — Project-specific Git configuration settings (remotes, branch settings, local configurations).
- 📄 `HEAD` — A file pointing to the current active branch (e.g. `ref: refs/heads/main` or `master`).
- 📄 `description` — Used only by the GitWeb program to describe the repo.

> ⚠️ **Never manually edit or delete the `.git` folder** — it would destroy your entire version history.

From this point on, Git will track **every change** you make inside this folder.

---

## 2.7 Configuring Git: User Name & Email

### Why is this needed?

When you make your **first commit**, Git needs to know **who** is making the changes. This information is attached to every commit in the project history.

If you haven't configured it, you'll see:
```
Please tell me who you are.
```

### Setting up globally (applies to all projects on your machine):

```bash
git config --global user.email "your-email@example.com"
git config --global user.name "Your Name"
```

### Setting up locally (applies only to the current project):

```bash
git config --local user.email "your-email@example.com"
git config --local user.name "Your Name"
```

### Verify your configuration:

```bash
git config --global user.name
git config --global user.email
```

### `--global` vs `--local`

| Flag | Scope | Use when... |
|------|-------|-------------|
| `--global` | Entire computer (all repos) | You use the same identity everywhere |
| `--local` | Current repository only | You use a different email for work vs personal |

> **Tip:** Set `--global` once when you install Git. Use `--local` only when you need a different identity for a specific project (e.g., work email vs personal email).

---

## 2.8 `git clone` — Cloning a Remote Repository

Instead of initializing a new repository from scratch, you can **clone** (download) an existing one from GitHub.

### Step-by-step:

1. Go to the repository on GitHub
2. Click the green **Code** button
3. Copy the **HTTPS** link
4. In your terminal:

```bash
git clone https://github.com/username/repository-name.git
```

**Output:**
```
Cloning into 'repository-name'...
remote: Enumerating objects: 10, done.
remote: Counting objects: 100% (10/10), done.
Receiving objects: 100% (10/10), done.
```

### What happens when you clone?

- A new folder is created with the repository name
- All files from the remote repo are downloaded
- A `.git` folder is created (the repo is fully initialized)
- The remote connection (called `origin`) is automatically set up

```bash
# Enter the cloned folder
cd repository-name

# See the files
ls

# Verify it's a Git repo (hidden .git folder exists)
ls -a
```

### Two ways to create a Git repository:

| Method | Command | When to use |
|--------|---------|-------------|
| **Initialize locally** | `git init` | Starting a brand-new project |
| **Clone from remote** | `git clone <url>` | Joining an existing project |

> No matter which method you choose, **initialization is always required** before you can start working with Git.

---

## 2.9 Creating a Remote Repository on GitHub

### Step-by-step:

1. Go to [github.com](https://github.com) and log in (create an account if needed)
2. Click the **green "New"** button (or the `+` icon → "New repository")
3. Fill in:
   - **Repository name** — e.g., `git-journey`
   - **Description** — e.g., "We are learning Git and GitHub"
   - **Visibility** — Public or Private
4. Click **Create repository**

> The repository is now created but **empty**. You can add files via the GitHub web interface or push files from your local machine.

---

## 📝 Key Takeaways

1. Install Git from [git-scm.com](https://git-scm.com) and verify with `git --version`
2. Use `git init` to start tracking a new project folder
3. Use `git clone <url>` to download an existing repository
4. Configure your name and email with `git config --global`
5. The hidden `.git` folder stores all tracking data — never delete it
6. You can create repositories **locally** (init) or on **GitHub** (clone)

---

[← Previous: Intro & Concepts](01_intro_and_concepts.md) | [Back to Index](../README.md) | [Next: Basic Workflow →](03_basic_workflow.md)
