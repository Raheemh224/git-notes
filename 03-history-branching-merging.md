### Chapter 3 : History, Branching & Merging 
## Viewing History 

Git gives you powerful tools to trace the history of your project. This is essential in DevOps and software development for debugging, auditing, and understanding changes over time. 

Let’s go through the most useful Git history commands you’ll regularly use. 

 

## 📜 Key Git History Commands 

🔍 `git log` 

Shows the full commit history of your repository. 

Useful for looking back at what’s been done and when. 

🧵 `git log --oneline --graph` 

A cleaner, condensed view of your commit history. 

Displays branches in a visual graph, great for understanding complex merges or release branches. 
 

📦 Commit Inspection Tools 

📄 `git show <commit-hash>` 

Displays details of a specific commit: 

- What was changed 
- Who made the change 
- The commit message 

`git show abc123`
 

 

🧾 Difference Comparison Tools 

✏️ `git diff` 

Compares your working directory (unstaged changes) with the last commit. 

Great for checking what you've modified before committing. 
 

📤 `git diff --staged` 

Compares your staged changes with the last commit. 

Shows exactly what you’re about to commit. 
 
 

🔎 Bonus Tools You’ll Love 

🙈 `git blame <file>` 

Shows who last modified each line in a file. 

Very useful for: 
- Debugging 
- Reviewing configuration files 
- Understanding why a change was made 

Despite the name, it’s more about accountability than actual blame. 
`git blame main.tf` 
 

🧙 `git reflog` 

One of Git’s most underrated tools. 

Shows every movement of HEAD, including: 
- Branch switches 
- Resets 
- Reflogs from deleted commits or branches 

Can help you recover lost work, such as after a bad rebase or accidental delete. 

 
## Why It Matters in DevOps 

These commands aren’t just for developers—they’re vital in DevOps workflows, where you're managing: 

- Infrastructure-as-Code (IaC) 
- Terraform modules 
- CI/CD pipelines 
- Helm charts and Kubernetes manifests 

When something breaks, Git history tools help you pinpoint what changed, when it changed, and who made the change. 

 

✅ Summary 

Understanding how to view Git history gives you visibility, control, and confidence when working with any kind of codebase. Whether you're debugging a pipeline or reviewing infrastructure updates, these commands will become your go-to tools. 

## Branching 101 

Branching is one of Git’s most powerful features. It allows you to work on multiple ideas or fixes at once, without affecting your main project. 

This is especially useful in DevOps workflows, where teams often juggle: 
- New features 
- Bug fixes 
- Experiments 
- Infrastructure changes 

 

🌿 What is a Branch? 

A branch is a lightweight, movable pointer to a specific commit. 

When you create a new branch, you’re essentially making a copy of the current state of the project. You can then: 

Test code safely 

Develop features in isolation 

Fix bugs without interfering with your main branch (e.g. main, master, or dev) 

 

## 💻 Essential Branching Commands 

- 📄 `git branch` 

Lists all local branches 

Can also be used to create a branch, but does not switch to it 

`git branch feature/login` 
 

- 🔄 `git switch -c <branch-name>` 

A more modern, beginner-friendly way to create and switch to a new branch in one step 

`git switch -c feature/login` 

 
 

- ↪️ `git switch <branch-name>` 

Switches to an existing branch 

`git switch dev` 
 

- 📼 `git checkout -b <branch-name>` 

An older method that creates and switches to a new branch 

Still works and widely used, though slightly less beginner-friendly 

git checkout -b feature/feed 
 

- 🗑️ `git branch -d <branch-name>` 

Deletes a branch once you're finished with it 

Git will warn you if the branch hasn’t been merged yet, to avoid data loss 

`git branch -d feature/login`
 

 

## 🧠 Checkout vs Switch – What’s the Difference? 

git switch: Modern, cleaner, and easier to understand 
 👉 Recommended for beginners (if your Git version supports it) 

git checkout: Older and more flexible 
 👉 Still useful, but can be more confusing due to how it handles both files and branches 

 

💡 Why Branching Matters 

- Fast and lightweight – Git branches don’t copy all files; they just point to commits 

- Encourages safe experimentation – try new features without risking the main codebase 

- Essential for team collaboration – everyone can work on separate branches and merge later 

- This flexibility is a big reason why Git is so widely adopted in DevOps and software teams. 

 

## Merging 

Merging is how we combine work from different branches in Git. Whether you’re working alone or as part of a DevOps team, merging is a fundamental part of collaboration. 

 

🔀 What Is Merging? 

When you’ve been working on a feature in a separate branch (e.g. feature/login) and want to bring those changes back into the main branch (e.g. main), you merge them. 

Basic merge syntax: 

git merge <branch-name> 
 

This takes the commits from the specified branch and applies them to your current branch. 

 

## ⚡ Two Types of Merges 

- ✅ 1. Fast-Forward Merge 

Happens when the target branch (e.g. main) has not changed since the feature branch was created. 

Git simply moves the pointer forward—no new commit is needed. 

Clean and simple. 

- 🔄 2. Recursive Merge (a.k.a. True Merge) 

Happens when both branches have new commits since they diverged. 

Git creates a merge commit to join both histories together. 

This helps preserve the complete timeline of both branches. 

 

## ⚔️ Merge Conflicts 

Sometimes, the same files or lines are modified in both branches. Git doesn’t know which version to keep, so you get a merge conflict. 

You’ll need to manually review and resolve the conflicting files. 

This is very common in collaborative work, especially with Infrastructure-as-Code and YAML files in DevOps. 

💡 Merge conflicts are not errors—they’re just Git’s way of saying: “I need your help to decide.” 

 

🧠 Visual Example

Let’s say: 

1. main has commits: A → B → C 

2. feature has commits: D → E (based off C) 

3. When you merge feature into main, Git combines the histories: 

A → B → C → D → E 
 

If both have new commits, Git will include a merge commit to tie them together. 

 

🤝 Why Merging Matters in DevOps 

Merging is the backbone of collaboration in Git. It's how: 

- Teams combine work safely 
- Features are brought into production 
- Infrastructure changes are integrated 
- CI/CD pipelines are triggered from merged code 

You’ll also see merging used in Pull Requests (PRs) or Merge Requests (MRs) on platforms like GitHub and GitLab. These are just user-friendly ways to request and review a merge. 

Visualise branches and logs 

## key Commands for Visualising Git History 

Here are a few useful commands for viewing the commit history and branch structure: 

`git log --oneline` 
 Displays a compact, one-line-per-commit view. It's clean, fast, and useful for a quick overview. 

`git log --oneline --graph` 
 Adds a visual tree structure, allowing you to see where branches have split or merged. 

`git log --oneline --graph --all` 
 This is arguably the most powerful version. It shows the complete commit history, across all branches, in a clear graphical format. 
 I personally call this the "GOAT" command — it's especially helpful when you're debugging issues, reviewing history, or collaborating with a team. 

Why Visualisation Matters 

These visual commands are particularly useful when: 

- 0 Merging branches and wanting to verify what actually happened. 
- Tracing the history of a feature or bug fix. 
- Explaining changes visually to others on your team or in a pull request (PR) review. 
- Debugging merge conflicts or unusual Git behaviour. 
- What Git Actually Tracks 

Git doesn't just track files — it tracks commits, each with a unique hash, forming a graph of your repository's history. 

For example: 

You start with an initial commit on main. 

You create a feature branch and add a few commits. 

Then you merge it back into main. 

The git log --graph view will visually display this entire flow, showing the point of the branch, each commit along the way, and where it was merged. 

Understanding this structure helps you gain clarity and confidence when working in teams, especially when reviewing pull requests or solving merge-related issues. 

## Rebase vs Merge 

A common topic in Git is the difference between rebase and merge. Both are used to integrate changes from one branch into another, but they work very differently under the hood. 

Let’s break it down in a simple and practical way. 

 

- 🔀 git merge – The Safe and Friendly Option 

Combines branches while preserving the full history 

Creates a merge commit that clearly shows when two branches were joined 

Useful in collaborative environments where it’s important to retain visibility of how the work happened 

Helps teams understand the sequence of events during development 

💬 Example: 
`git merge feature/login` 
 

🧠 Think of merge as: 

“Let’s join the two branches and keep the whole story.” 

 

- 🧼 git rebase – The Clean and Surgical Option 

Rewrites the commit history so it appears as though your work was based on the latest version of the target branch 

Produces a linear, cleaner timeline – no merge commits 

Great for tidying up your branch before opening a Pull Request 

Ideal for making your history more readable, especially after several messy or experimental commits 

💬 Example: 
`git rebase main` 
 

🧠 Think of rebase as: 

“Let’s clean up the history and pretend my branch started from the latest commit.” 

 

🤔 When Should You Use Each? 

✅ Use merge: 

- When collaborating with a team 
- To preserve full commit history 
- On shared branches or in open-source projects 

🧹 Use rebase: 

- When you're cleaning up your own feature branch 
- Before pushing or opening a Pull Request 
- To create a clean, readable commit timeline 

 

⚠️ Important Rule: Never Rebase Shared Branches 

Rebasing rewrites history. If someone else is working on the same branch and you rebase it, you could: 

- Break their changes 
- Cause major conflicts 
- Create confusion across the team 

🛑 Do not rebase public/shared branches like main, dev, or any collaboration branch. 
