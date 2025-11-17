# Git & GitHub Workflow - Essential Guide

> **"Git is your time machine. GitHub is your portfolio. Master both."**

---

## 🎯 What is Git vs GitHub?

### **Git** = Version control system (the tool)
- Runs on your computer
- Tracks changes to your code
- Like "undo" on steroids
- Works offline

### **GitHub** = Cloud hosting for Git (the service)
- Stores your code online
- Collaboration platform
- Portfolio for developers
- Requires internet

**Think of it like:**
- **Git** = Microsoft Word
- **GitHub** = Google Docs

---

## 📚 Core Git Concepts

### 1. **Repository (Repo)**
A folder that Git is tracking.

```bash
git init  # Turn current folder into a repo
```

### 2. **Commit**
A saved snapshot of your code at a point in time.

```
[Commit 1] → [Commit 2] → [Commit 3] → [Latest]
"Added nav" "Fixed bug"  "New feature"
```

### 3. **Branch**
A separate timeline of commits (for working on features).

```
main branch:    A → B → C → D
                     ↓
feature branch:      E → F (merge back to main)
```

### 4. **Remote**
A version of your repo stored online (usually on GitHub).

---

## 🎨 Your First Git Workflow

### Step 1: Create a Repository

```bash
# Create a new folder
mkdir my-project
cd my-project

# Initialize Git
git init

# Check status
git status
```

### Step 2: Make Some Changes

```bash
# Create a file
echo "# My Project" > README.md
```

### Step 3: Stage Changes

```bash
# Stage specific file
git add README.md

# Or stage everything
git add .
```

**Staging = preparing files for commit** (like putting items in a shopping cart before checkout)

### Step 4: Commit Changes

```bash
git commit -m "Initial commit with README"
```

**Commit message should be clear and descriptive!**

### Step 5: View History

```bash
git log
```

---

## 🔧 Essential Git Commands

### **Status & Information**

```bash
git status              # See what's changed
git log                 # View commit history
git log --oneline       # Compact history
git diff                # See unstaged changes
git diff --staged       # See staged changes
```

### **Making Commits**

```bash
git add filename.txt    # Stage specific file
git add .               # Stage all changes
git commit -m "message" # Commit with message
git commit -am "msg"    # Stage + commit (tracked files only)
```

### **Branching**

```bash
git branch              # List branches
git branch feature-nav  # Create new branch
git checkout feature-nav # Switch to branch
git checkout -b feature # Create AND switch (shortcut)
git branch -d feature   # Delete branch (safe)
git branch -D feature   # Force delete branch
```

### **Merging**

```bash
# From feature branch back to main:
git checkout main
git merge feature-nav
```

### **Undoing Things**

```bash
# Unstage file (keep changes)
git restore --staged filename.txt

# Discard changes to file (DANGER!)
git restore filename.txt

# Undo last commit (keep changes)
git reset HEAD~1

# Undo last commit (discard changes) (DANGER!)
git reset --hard HEAD~1
```

---

## 🌐 GitHub Workflow

### **Connect Local Repo to GitHub**

1. Create a new repo on GitHub.com
2. Copy the repo URL
3. Link it:

```bash
git remote add origin https://github.com/username/repo-name.git
git branch -M main
git push -u origin main
```

### **Push Changes**

```bash
git push  # Push to remote
```

### **Pull Changes**

```bash
git pull  # Get latest changes from remote
```

### **Clone Existing Repo**

```bash
git clone https://github.com/username/repo-name.git
cd repo-name
```

---

## 🎯 Professional Workflow (Feature Branch Pattern)

```bash
# 1. Start from main branch
git checkout main
git pull  # Make sure you have latest

# 2. Create feature branch
git checkout -b feature/user-authentication

# 3. Make changes, commit often
git add .
git commit -m "Add login form"

git add .
git commit -m "Add authentication logic"

# 4. Push feature branch to GitHub
git push -u origin feature/user-authentication

# 5. Create Pull Request on GitHub
# (Done in browser at GitHub.com)

# 6. After PR is approved and merged, clean up
git checkout main
git pull
git branch -d feature/user-authentication
```

---

## ✍️ Writing Good Commit Messages

### **Bad Commit Messages:**
```bash
git commit -m "fixed stuff"
git commit -m "updates"
git commit -m "asdf"
git commit -m "bug fix"
```

### **Good Commit Messages:**
```bash
git commit -m "Fix navigation menu closing on mobile"
git commit -m "Add user authentication with JWT"
git commit -m "Update README with installation instructions"
git commit -m "Refactor API calls into custom hooks"
```

### **Format:**
```
Verb in present tense + what you did

Examples:
- Add ...
- Update ...
- Fix ...
- Remove ...
- Refactor ...
```

---

## 🎨 Common Workflows

### **Daily Development Flow**

```bash
# Morning: Get latest changes
git pull

# Work on feature
# ... make changes ...
git add .
git commit -m "Add feature description"

# End of day: Push to backup
git push
```

### **Working on a Feature**

```bash
# Create feature branch
git checkout -b feature/dark-mode

# Make changes and commit frequently
git add .
git commit -m "Add dark mode toggle button"

git add .
git commit -m "Implement dark mode styles"

# Push feature branch
git push -u origin feature/dark-mode

# Create Pull Request on GitHub
```

### **Fixing a Bug**

```bash
# Create bug fix branch
git checkout -b fix/login-error

# Fix the bug
git add .
git commit -m "Fix login error when email is empty"

# Push and create PR
git push -u origin fix/login-error
```

---

## 🐛 Common Git Problems & Solutions

### **Problem: I committed to the wrong branch!**

```bash
# If you haven't pushed:
git reset HEAD~1  # Undo commit (keeps changes)
git stash         # Save changes temporarily
git checkout correct-branch
git stash pop     # Apply changes
git add .
git commit -m "message"
```

### **Problem: I need to undo my last commit**

```bash
# Keep changes, just undo commit
git reset HEAD~1

# Discard changes completely (DANGER!)
git reset --hard HEAD~1
```

### **Problem: Merge conflict!**

```bash
# After git merge or git pull:
# 1. Open conflicted files in VS Code
# 2. Look for conflict markers:

<<<<<<< HEAD
Your changes
=======
Their changes
>>>>>>> branch-name

# 3. Edit file to keep what you want
# 4. Remove conflict markers
# 5. Stage and commit:
git add .
git commit -m "Resolve merge conflict in filename.js"
```

### **Problem: I want to discard all local changes**

```bash
git restore .  # Discard unstaged changes
git reset --hard origin/main  # Match remote exactly (DANGER!)
```

### **Problem: I accidentally committed sensitive info!**

```bash
# If you HAVEN'T pushed yet:
git reset HEAD~1  # Undo commit
# Remove sensitive info from files
git add .
git commit -m "message"

# If you HAVE pushed:
# You're in trouble. Change all passwords/keys immediately.
# Contact GitHub support to purge from history.
```

---

## 📁 .gitignore File

**Never commit these files:**

```
# .gitignore

# Dependencies
node_modules/
package-lock.json

# Environment variables
.env
.env.local
.env.production

# Build output
dist/
build/
.next/

# IDE
.vscode/
.idea/
*.swp

# OS files
.DS_Store
Thumbs.db

# Logs
*.log
npm-debug.log*

# Secrets
config/secrets.js
*.pem
```

**Add .gitignore BEFORE your first commit!**

---

## 🎯 GitHub Features

### **1. Pull Requests (PRs)**

- Way to propose changes
- Code review before merging
- Discussion and feedback

**How to create:**
1. Push branch to GitHub
2. Go to repo on GitHub.com
3. Click "New Pull Request"
4. Select your branch
5. Add description
6. Create PR

### **2. Issues**

- Track bugs and features
- Assign to team members
- Reference in commits:

```bash
git commit -m "Fix login bug (fixes #23)"
```

### **3. README.md**

**Your repo's front page!** Should include:
- Project description
- Installation instructions
- Usage examples
- Screenshots
- License

### **4. GitHub Pages**

Free hosting for static sites!

```bash
# Enable in repo settings
# Your site: https://username.github.io/repo-name
```

---

## ✏️ Practice Exercise

**Create a portfolio project on GitHub:**

1. Create a new folder `my-portfolio`
2. Initialize Git
3. Create `index.html`, `style.css`, `script.js`
4. Create README.md
5. Add .gitignore
6. Make initial commit
7. Create GitHub repo
8. Push to GitHub
9. Create a new branch `feature/contact-form`
10. Add a contact form
11. Commit changes
12. Push branch
13. Create Pull Request
14. Merge PR
15. Delete feature branch

<details>
<summary>Solution</summary>

```bash
# 1. Create folder
mkdir my-portfolio
cd my-portfolio

# 2. Initialize Git
git init

# 3. Create files
echo "<!DOCTYPE html><html><head><title>Portfolio</title></head><body><h1>My Portfolio</h1></body></html>" > index.html
echo "body { font-family: Arial; }" > style.css
echo "console.log('Hello');" > script.js

# 4. Create README
echo "# My Portfolio\n\nPersonal portfolio website." > README.md

# 5. Create .gitignore
echo "node_modules/\n.env\n.DS_Store" > .gitignore

# 6. Initial commit
git add .
git commit -m "Initial commit with basic structure"

# 7-8. Create GitHub repo and push
# (Do this on GitHub.com, then:)
git remote add origin https://github.com/yourusername/my-portfolio.git
git branch -M main
git push -u origin main

# 9. Create feature branch
git checkout -b feature/contact-form

# 10-11. Add contact form and commit
echo "<form><input type='email' placeholder='Email'><button>Send</button></form>" >> index.html
git add index.html
git commit -m "Add contact form"

# 12. Push branch
git push -u origin feature/contact-form

# 13-14. Create and merge PR
# (Do this on GitHub.com)

# 15. Delete feature branch
git checkout main
git pull
git branch -d feature/contact-form
```

</details>

---

## 🎯 Git Cheat Sheet

```bash
# SETUP
git init                    # Initialize repo
git clone <url>             # Clone remote repo

# DAILY WORKFLOW
git status                  # Check status
git add .                   # Stage all changes
git commit -m "message"     # Commit changes
git push                    # Push to remote
git pull                    # Pull from remote

# BRANCHING
git branch                  # List branches
git branch <name>           # Create branch
git checkout <name>         # Switch branch
git checkout -b <name>      # Create and switch
git merge <branch>          # Merge branch

# UNDO
git restore <file>          # Discard changes
git restore --staged <file> # Unstage file
git reset HEAD~1            # Undo last commit

# INFO
git log                     # View history
git log --oneline           # Compact history
git diff                    # See changes
```

---

## 🎯 Key Takeaways

1. **Commit often** (small, logical commits)
2. **Write clear commit messages** (future you will thank you)
3. **Never commit secrets** (.env files, API keys)
4. **Use branches for features** (keep main clean)
5. **Pull before you push** (avoid conflicts)
6. **GitHub is your portfolio** (make it look good!)

---

## 📚 Learn More

- **Git Documentation:** https://git-scm.com/doc
- **GitHub Guides:** https://guides.github.com/
- **Interactive Git Tutorial:** https://learngitbranching.js.org/

---

**Git is the most important tool in a developer's toolkit. Practice it daily.** 🚀
