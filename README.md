# Git Commands - Complete Guide

## Step 1: Git Setup

### 1. Check Git Version
```bash
git --version
```

### 2. Configure Global Settings
Set your name and email before using Git for the first time:

```bash
# Set your name (for all repositories)
git config --global user.name "mubin"

# Set your email
git config --global user.email "example@gmail.com"
```

If you want to set config only for this repository (remove --global):
```bash
git config user.name "mubin"
git config user.email "example@gmail.com"
```

Verify your configuration:
```bash
git config user.name
git config user.email
```

---

## Core Git Workflow (Add, Commit, Push, Pull)

### The Steps:
1. **Add** → Stage your files (tell Git what has changed)
2. **Commit** → Save your changes (record in Git)
3. **Push** → Upload commits to remote repository (send to GitHub)
4. **Pull** → Download changes from remote repository (get others' work)

---

## Starting a Repository

### Create a New Repository:
```bash
# Create new folder
mkdir my-project
cd my-project

# Initialize git repository
git init
```

### Or Clone Existing Repository from GitHub:
```bash
# Clone from GitHub
git clone <url> <new-folder-name>

# Example:
git clone https://github.com/user/repo.git my-repo
```

---

## Checking Status

### View Repository Status:
```bash
git status
```

This shows:
- Which files have been modified
- Which files are in staging area
- Which files are untracked (Git not tracking them)

**Important:** `git status` only works inside a repository folder, not outside it.

---

## Add and Commit - Saving Your Work

### Add Files to Staging Area:
```bash
# Add all files
git add .

# Or add specific file
git add filename.txt
git add src/

# View staged files
git status
```

### Create a Commit:
```bash
# Commit staged files with message
git commit -m "Your commit message"

# Examples:
git commit -m "Add login feature"
git commit -m "Fix bug in user profile"
```

### Add and Commit Together:
```bash
# Commit all tracked files that were modified
# (new untracked files will NOT be committed)
git commit -a -m "Update features"
```

---

## Viewing Commits and Changes

### View All Commits:
```bash
# View all commits
git log

# View in one-line format
git log --pretty=oneline

# View last 5 commits
git log -n 5

# View with detailed changes
git log -p
git log -p -n 2  # Last 2 commits with changes

# View statistics summary
git log --stat

# View commits from specific time period
git log --since="2 days ago"
git log --since="1 week ago"
```

### Compare File Changes:
```bash
# Compare working directory with staging area
git diff

# Compare staging area with last commit
git diff --staged
```

---

## Remote Repository (Working with GitHub)

### Add Remote Repository:
```bash
# Connect GitHub repository to your local repository
git remote add origin <url>

# Example:
git remote add origin https://github.com/user/repo.git
```

### View Remote Information:
```bash
# List all remotes
git remote

# View detailed info (push/pull locations)
git remote -v
```

### Push to GitHub:
```bash
# Push commits to GitHub (first time)
git push -u origin master
# (use -u flag first time, then just 'git push' works)

# After first time, just use:
git push

# Or push to specific branch:
git push origin branchname

# Delete remote branch:
git push -d origin branchname
```

### Pull from GitHub:
```bash
# Download latest commits and merge
git pull

# Or use rebase for linear history
git pull --rebase origin master
```
# Git Pull with Rebase

Fetches changes from the remote `origin` repository's `master` branch and reapplies local commits on top of the fetched changes, creating a linear commit history instead of a merge commit.

**Usage:**
- Use this command when you want to maintain a clean, linear project history
- Useful in collaborative workflows to avoid unnecessary merge commits
- Rewrites local commit history, so use with caution on shared branches

**Note:** This performs a rebase operation, which rewrites commit history. Only use on local branches that haven't been pushed or shared with others.

---

## Working with Branches

### Create New Branch:
```bash
# Create new branch from current branch
git branch feature-new-ui

# Create and switch to new branch at same time
git checkout -b feature-new-ui
```

### View All Branches:
```bash
# List all branches
git branch

# List with detailed info (commit hash and message)
git branch -v
```

### Switch Between Branches:
```bash
git checkout feature-new-ui
git checkout master
git checkout main
```

### Delete Branch:
```bash
# Delete merged branch
git branch -d feature-new-ui

# Force delete (even if not merged)
git branch -D feature-new-ui
```

---

## Merging Branches

### Merge Two Branches:
```bash
# First, switch to master/main
git checkout master

# Then merge other branch
git merge feature-new-ui
```

### Check Merge Status:
```bash
# View already merged branches
git branch --merged

# View branches not yet merged
git branch --no-merged
```

---

## File Operations

### Rename File:
```bash
# Rename tracked file (stages it)
git mv old-filename.txt new-filename.txt
```

### Delete File:
```bash
# Simple delete (Git still tracks it)
rm filename.txt

# Delete through Git (stages it)
git rm filename.txt

# Force delete of new file already staged
git rm -f filename.txt

# Remove only from staging area (keeps in working directory)
git rm --cached filename.txt
```

### Revert Changes:
```bash
# Restore modified file to last commit state
git checkout -- filename.txt

# Revert all modified files
git checkout -f

# Remove file from staging area (keeps in working directory)
git restore --staged filename.txt
```

---

## .gitignore File - Ignoring Files

Put filenames in `.gitignore` to prevent Git from tracking them. Place this file in project root.

### .gitignore Rules:
```
# Ignore specific file
config.txt
secrets.env

# Ignore all files with specific extension
*.log
*.tmp
*.pyc

# Ignore specific folder
node_modules/
.git/
build/

# Ignore folder only in root
/config/private/

# Ignore folder in subdirectory
secondfolder/firstfolder
```

**Important:** If a file was already tracked when you add it to `.gitignore`, you must use `git rm --cached filename` to untrack it first. Then `.gitignore` will work.

---

## Modifying Commits

### Amend Last Commit:
```bash
# Add new files to last commit or change message
git add .
git commit --amend -m "Updated commit message"

# Change only message (without adding files)
git commit --amend -m "New message"
```

This opens vim editor. Press `i` to edit, then `Esc` → `:wq` to save and exit.

---

## SSH Keys for Remote Push

### Generate SSH Key:
```bash
# Check if SSH keys exist
# macOS/Linux:
ls ~/.ssh/id_rsa

# Windows PowerShell:
dir C:\Users\YourUsername\.ssh
```

If exists, add it to GitHub directly. If not, follow GitHub documentation:
[Generating a new SSH key and adding it to the ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

---

## Creating Command Shortcuts (Aliases)

```bash
# Create shortcuts for frequently used commands
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.unstage 'restore --staged --'
git config --global alias.last 'log -p -1'

# Now use:
git st          # instead of git status
git co -b dev   # instead of git checkout -b dev
git unstage filename  # to remove from staging area
```

---

## Daily Workflow Example

```bash
# 1. Create new branch
git checkout -b feature/add-login

# 2. Do your work - create/modify files
# ... your code ...

# 3. Check status
git status

# 4. Add files
git add .

# 5. Commit
git commit -m "Add login form"

# 6. Push to remote
git push -u origin feature/add-login

# 7. Create PR on GitHub and merge
# 8. Switch to master/main and pull
git checkout master
git pull
```

---

## Useful Terminal Commands

```bash
pwd                 # Show current directory path
ls                  # List files in current directory
ls -la              # List with hidden files and details
mkdir foldername    # Create new folder
touch filename.txt  # Create empty file
cat filename.txt    # View file contents
cd foldername       # Enter folder
cd ..               # Go to parent folder
clear               # Clear terminal
```

### Windows PowerShell Commands:
```powershell
pwd                 # Show current directory
ls                  # List files and folders
mkdir foldername    # Create new folder
touch filename.txt  # Create file (may not work on Windows)
New-Item -Path filename.txt -ItemType File  # Create file (Windows way)
```

---

## Quick Reference Table

| Command | Purpose |
|---------|---------|
| `git init` | Create new repository |
| `git clone <url>` | Download repository |
| `git status` | Check status |
| `git add .` | Stage all files |
| `git commit -m ""` | Create commit |
| `git push` | Send to GitHub |
| `git pull` | Get from GitHub |
| `git branch` | List branches |
| `git checkout -b <name>` | Create and switch branch |
| `git merge <branch>` | Merge branches |
| `git log` | View commit history |
| `git diff` | View changes |

---

## Important Warning

```bash
# DANGER: Deletes all git history - DO NOT RUN unless you know what you're doing!
rm -rf .git
```

---

## Resources

- [Git Official Book](https://git-scm.com/book)
- [GitHub Documentation](https://docs.github.com/)
- [Git Documentation](https://git-scm.com/doc)
- [GitButler Blog](https://blog.gitbutler.com/)
- [So you think you know git? - Scott Chacon](https://git-scm.com/book)
