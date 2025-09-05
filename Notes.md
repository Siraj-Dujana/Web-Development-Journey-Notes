# 🚀 Git & GitHub Notes

## 🔹 What is Git?

* **Git** is an open-source **version control system** tool.
* Helps track changes in code:

  * When and what changes were made.
  * View full history of the project.
* Supports **collaboration** among developers.

---

## 🔹 What is GitHub?

* **GitHub** is a website/platform where repositories are hosted online.
* Types of Repositories:

  * **Public:** Visible to everyone, but you choose who can commit.
  * **Private:** You control who can see and contribute.

---

## 📄 README.md

* A markdown file in a repo that explains the project:

  * Title & description
  * Installation steps
  * Usage instructions
  * Contribution guidelines
* **Red vs Green (diff colors):**

  * 🟢 **Green** = Added lines/new content
  * 🔴 **Red** = Removed/deleted content

---

## 📝 Commit

* A **commit** = A saved change in version history.
* Process:

  1. **Stage** changes → `git add`
  2. **Commit** changes → `git commit`
* Example:

  ```bash
  git add .
  git commit -m "Updated login feature"
  ```

---

## 🖥️ GitHub Desktop Terminologies

* **Repository:** Central storage for project + version history.
* **Collaborators:** Team members working on project.
* **Commit:** Save snapshot of changes locally.
* **Push:** Upload committed changes → remote repo.
* **Pull:** Download & merge changes → local repo.
* **Stash:** Temporarily save uncommitted changes.
* **Clone:** Copy remote repo → local machine.
* **Branch:** Independent line of development.

---

## ⚙️ Git Setup

### Installation

* Install **VS Code** & **Git Bash**
* Check version:

  ```bash
  git --version
  ```

### Configuring Git

* Global config:

  ```bash
  git config --global user.name "Your Name"
  git config --global user.email "you@example.com"
  ```
* View settings:

  ```bash
  git config --list
  ```

---

## 🔄 Local vs Remote

* **Local repo:** Stored on your system.
* **Remote repo:** Stored on GitHub.

Workflow:

```
clone → add → commit → push
```

---

## 📌 Git Commands

### Clone

```bash
git clone <repo-link>
```

### Status

```bash
git status
```

* **Untracked:** New files
* **Modified:** Changed
* **Staged:** Ready to commit
* **Unmodified:** Unchanged

### Add & Commit

```bash
git add <file-name>
git add .        # add all
git commit -m "message"
```

### Push

```bash
git push origin main
```

### Init (New Repo)

```bash
git init
git remote add origin <repo-link>
git branch -M main
git push -u origin main
```

---

## 🌿 Git Branches

* Create new branch:

  ```bash
  git checkout -b feature-branch
  ```
* Switch branch:

  ```bash
  git checkout main
  ```
* Delete branch:

  ```bash
  git branch -d branch-name
  ```

---

## 🔀 Merging Code

### Way 1 (Direct Merge)

```bash
git diff branch-name     # compare
git merge branch-name    # merge
```

### Way 2 (Pull Request)

* Create a **PR** → Notify others about your branch changes.

---

## 📥 Pull Command

* Fetch & update local repo:

```bash
git pull origin main
```

---

## ⚠️ Merge Conflicts

* Happen when Git cannot auto-resolve differences.
* Must manually fix conflicting code.

---

## 🔄 Undoing Changes

1. **Staged changes (unstage):**

   ```bash
   git reset <file>
   ```
2. **Undo last commit:**

   ```bash
   git reset HEAD~1
   ```
3. **Undo many commits:**

   ```bash
   git reset <commit-hash>
   git reset --hard <commit-hash>
   ```

View commit history:

```bash
git log
```

---

## 🍴 Fork

* A **fork** = Copy of another repository.
* Allows you to modify without affecting original repo.

---

## 💻 Terminal Basics

* `pwd` → Print working directory
* `cd folder` → Move inside folder
* `cd ..` → Move back
* `ls` → Show files
* `ls -a` → Show hidden files
* `mkdir new-folder` → Create new folder
* `clear` → Clear terminal

---

✅ **End of Notes – You’re Git Ready!** 🚀
