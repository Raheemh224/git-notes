# Chapter 2: Git Internals and Core Concepts

---

## 📘 Git Terminology

### 📁 Repository (or Repo)
- A Git repository is a folder that Git is tracking.
- If a folder contains a hidden `.git` directory, it's a Git repository.
- This `.git` folder stores all metadata and project history.

### 📝 Commit
- A snapshot of your project at a given point in time.
- Includes:
  - The current state of the files.
  - Metadata (author, timestamp, message).
  - A pointer to the parent commit (previous version).

### 🌿 Branch
- A branch is a pointer to a specific commit.
- The default branch is often called `main` or `master`.
- Branches allow isolated work without affecting the main codebase.
- Feature branches use names like `feature/login`.

### 🌐 Remote
- A remote refers to a version of your repo hosted elsewhere (e.g., GitHub, GitLab, Bitbucket).
- The default remote is usually named `origin`.

### 📦 Staging Area (Index)
- A buffer between editing and committing.
- Use `git add` to stage changes, and `git commit` to snapshot them.

### 🔘 Blobs (Binary Large Objects)
- Git stores file contents as blobs.
- File names don't matter—only content does.
- Identical content always gets the same SHA-1 hash.

### 🌲 Trees
- Trees represent folders and directory structure.
- They link to blobs (files) and other trees (subfolders).

### 🏷️ Refs (References)
- Pointers to commits.
- Includes:
  - Branches
  - Tags
  - Special references like `HEAD`

### 🎯 HEAD
- The current position in your repo.
- Usually points to the latest commit on your checked-out branch.
- Git updates `HEAD` whenever you switch branches or make new commits.

---

## 🗂️ Git’s Internal Files & Structure

### 🧠 What’s Inside the `.git` Directory?

> The `.git` folder is the brain of your Git repository.

#### 📂 .git/refs
- Stores branch and tag references.

#### 🧱 .git/objects (Object Store)
- Stores all your blobs, trees, and commits.
- All content is compressed and hashed using SHA-1.

#### ⚙️ .git/config
- Stores settings like:
  - User name
  - Email
  - Remote URLs
- Config is repo-specific.

#### 🎯 .git/HEAD
- Tracks the current branch or commit.
- If corrupted, Git can get confused.

#### 📦 .git/index
- Git’s on-disk staging area.
- Prepares your next commit based on staged changes.

### ⚠️ Why the `.git` Folder Matters
- If deleted or damaged:
  - You lose history, branches, configs, and tracking.
- “No `.git`, no Git.”

ls-a
##


---

### Common Git Commands

- `git init` — Initialise a new Git repository
- `git add` — Stage changes for the next commit
- `git commit` — Save a snapshot of staged changes
- `git status` — Show the state of the working directory and staging area
- `git log` — Display commit history
- `git diff` — Show changes between commits or the working directory
- `git config` — Set Git configuration options (user, email, etc.)
- `git help <command>` — View built-in documentation for a command
- `git clone` — Copy a remote repository locally
- `git rm` — Remove files from the working directory and staging area
- `git mv` — Rename or move a file
- `git restore` — Restore working directory files

## 🔁 The Three Areas of Git

Understanding Git’s core workflow prevents common mistakes.

---

### 1️⃣ Working Directory

- This is where you actively edit files using your code editor.
- It could be Python scripts, Terraform modules, or Kubernetes manifests.
- Changes made here are **not tracked by Git** until you explicitly tell Git to track them.
- The working directory reflects the current state of your project.

---

### 2️⃣ Staging Area (Index)

- A preparation zone for your next commit.
- Think of it as a clipboard where you collect the changes you want to save.
- You move changes here using:

## 3️⃣ Repository
This is your local .git directory where Git stores your commit history.

When you run:

`git commit -m "Your message"`
Git takes everything from the staging area and saves it as a snapshot.

The repository contains:
✅ Commits (snapshots)

✅ Tags and branches

✅ Configuration files

✅ The object store

✅ Logs and references

## 📊 Git Workflow

[Working Directory] → (git add) → [Staging Area] → (git commit) → [Repository]
💡 Note: Saving a file in your editor does not mean Git is tracking it.

You must use:
`git add`
`git commit`
to include changes in your Git history.

💡 Why This Matters

This flow is consistent no matter what kind of project you're working on:

💻 Application development

⚙️ Infrastructure as Code (Terraform, Ansible, etc.)

🔄 CI/CD pipelines

🧪 Feature testing branches

Understanding how changes flow through these areas will help you:

✅ Track changes confidently

✅ Avoid staging or committing the wrong files

✅ Recover or roll back changes safely

✅ Collaborate effectively in team environments

✅ Final Summary
Git uses three main areas to manage project changes:

Working Directory – where you make edits

Staging Area (Index) – where you prepare commits

Repository – where commits are permanently stored

The .git directory is the heart of the repository and contains everything Git needs to function.

🔁 Git Flow Recap

Edit → Stage → Commit

🔑 Key Characteristics of Git

📸 Snapshot-based — not just a file tracker

🔐 Uses SHA-1 hashes to identify file contents uniquely

⚡ Fast, efficient, and distributed by design