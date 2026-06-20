# Module 7: Git & GitHub Cheat Sheet

---

## 🔧 Setup & Configuration

| Command | Description |
|---------|-------------|
| `git --version` | Check installed Git version |
| `git config --global user.name "Name"` | Set your name globally |
| `git config --global user.email "email"` | Set your email globally |
| `git config --local user.name "Name"` | Set name for current repo only |
| `git config --list` | View all configuration settings |

---

## 📁 Creating Repositories

| Command | Description |
|---------|-------------|
| `git init` | Initialize a new Git repo in current folder |
| `git clone <url>` | Clone (download) a remote repository |

---

## 📊 Checking Status & History

| Command | Description |
|---------|-------------|
| `git status` | Show changed/staged/untracked files |
| `git log` | Show full commit history |
| `git log --oneline` | Show compact commit history |
| `git log --graph --oneline` | Show history as a visual graph |
| `git diff` | Show unstaged changes |
| `git diff --staged` | Show staged changes |
| `git diff branch1..branch2` | Compare two branches |
| `git reflog` | Show all HEAD movements (safety net) |

---

## ➕ Staging Changes

| Command | Description |
|---------|-------------|
| `git add <file>` | Stage a specific file |
| `git add .` | Stage all changes in current directory + subdirs |
| `git add --all` or `git add -A` | Stage ALL changes across entire project |
| `git add *` | Stage new/modified files (NOT deleted) |
| `git add *.txt` | Stage all `.txt` files in current directory |
| `git reset` | Unstage all changes (keep file contents) |
| `git reset <file>` | Unstage a specific file |

---

## 💾 Committing

| Command | Description |
|---------|-------------|
| `git commit -m "message"` | Commit staged changes with a message |
| `git commit -am "message"` | Stage all tracked files AND commit (shortcut) |
| `git commit --amend` | Modify the last commit (message or content) |

---

## ↩️ Undoing Changes

| Command | Description |
|---------|-------------|
| `git reset HEAD~` | Undo last commit, keep changes (unstaged) |
| `git reset --soft HEAD~` | Undo last commit, keep changes (staged) |
| `git reset --hard` | Undo last commit AND discard all changes |
| `git reset --hard <commit-id>` | Reset to a specific commit (⚠️ destructive) |
| `git checkout -- <file>` | Discard unstaged changes in a file |
| `git restore <file>` | Discard unstaged changes (modern syntax) |
| `git restore --staged <file>` | Unstage a file (modern syntax) |

---

## 🗑️ Deleting Files

| Command | Description |
|---------|-------------|
| `git rm <file>` | Delete file + stage the deletion |
| `git rm -f <file>` | Force delete (even with local changes) |
| `git rm --cached <file>` | Untrack file but keep it on disk |
| `git rm -r <folder>` | Recursively delete folder + contents |

---

## 🌿 Branching

| Command | Description |
|---------|-------------|
| `git branch` | List all local branches |
| `git branch -a` | List all branches (local + remote) |
| `git branch <name>` | Create a new branch |
| `git checkout <name>` | Switch to a branch |
| `git switch <name>` | Switch to a branch (modern syntax) |
| `git checkout -b <name>` | Create + switch to a new branch |
| `git switch -c <name>` | Create + switch (modern syntax) |
| `git branch -d <name>` | Delete a merged branch |
| `git branch -D <name>` | Force delete any branch |
| `git branch -m <new-name>` | Rename current branch |

---

## 🔀 Merging & Rebasing

| Command | Description |
|---------|-------------|
| `git merge <branch>` | Merge a branch into current branch |
| `git merge --abort` | Cancel a merge in progress |
| `git rebase <branch>` | Rebase current branch onto another |
| `git rebase -i HEAD~n` | Interactive rebase (edit last n commits) |
| `git rebase --abort` | Cancel a rebase in progress |

---

## 📦 Stashing

| Command | Description |
|---------|-------------|
| `git stash` | Save uncommitted changes temporarily |
| `git stash save "message"` | Stash with a descriptive name |
| `git stash pop` | Restore most recent stash + remove it |
| `git stash apply` | Restore most recent stash + keep it |
| `git stash list` | Show all saved stashes |
| `git stash apply stash@{n}` | Restore a specific stash |
| `git stash drop stash@{n}` | Delete a specific stash |
| `git stash clear` | Delete ALL stashes |

---

## 🌐 Remote Repositories

| Command | Description |
|---------|-------------|
| `git remote -v` | View remote connections |
| `git remote add origin <url>` | Add a remote named "origin" |
| `git remote set-url origin <url>` | Change remote URL |
| `git remote remove <name>` | Remove a remote |
| `git push -u origin main` | Push + set upstream (first time) |
| `git push` | Push to default upstream |
| `git push origin <branch>` | Push a specific branch |
| `git push --force` | Force push (⚠️ overwrites remote) |
| `git pull` | Fetch + merge from remote |
| `git pull origin <branch>` | Pull a specific branch |
| `git fetch` | Download changes without merging |
| `git fetch origin` | Fetch from a specific remote |

---

## 🏷️ Tags

| Command | Description |
|---------|-------------|
| `git tag` | List all tags |
| `git tag <name>` | Create a lightweight tag |
| `git tag -a <name> -m "msg"` | Create an annotated tag |
| `git push origin <tag>` | Push a specific tag |
| `git push origin --tags` | Push all tags |
| `git tag -d <name>` | Delete a local tag |

---

## 🚫 `.gitignore` Patterns

| Pattern | Meaning |
|---------|---------|
| `filename` | Ignore a specific file |
| `folder/` | Ignore an entire folder |
| `*.ext` | Ignore all files with extension |
| `!keep.ext` | Exception — do NOT ignore this file |
| `**/logs` | Ignore `logs` anywhere in project |
| `doc/*.txt` | Ignore `.txt` only in `doc/` folder |

---

## 🔁 Common Workflows

### Daily Workflow:
```bash
git status          # Check what changed
git add .           # Stage everything
git commit -m "msg" # Save permanently
git push            # Upload to GitHub
```

### Starting a New Feature:
```bash
git checkout -b feature/name   # Create feature branch
# ... do work ...
git add .
git commit -m "Add feature"
git push origin feature/name
# Create Pull Request on GitHub
```

### Updating Your Branch:
```bash
git checkout main
git pull
git checkout feature/name
git merge main    # or: git rebase main
```

### Resolving Merge Conflicts:
```bash
git merge feature-branch        # Conflict occurs
# Edit conflicted files, remove markers
git add .
git commit -m "Resolve conflicts"
```

---

[← Previous: GitHub & Collaboration](06_github_collaboration.md) | [Back to Index](../README.md)
