### Chapter 4 – Advanced Git Usage  

## Git Stash and Pop 

Imagine you're halfway through updating a script or tweaking a config file—and suddenly you're asked to switch to another branch to handle something urgent. 
 But you're not ready to commit yet, and the code might not even work. 

This is exactly where git stash becomes a lifesaver. 

 

🎒 What Is git stash? 

Think of git stash as a temporary storage box for your unfinished changes. It lets you pause your work, switch tasks, and come back later—without losing progress or committing incomplete work. 

 

## 📦 Key git stash Commands 

- ✅ git stash 

Saves all uncommitted changes (both staged and unstaged) 

Cleans your working directory so you can safely switch branches 

Think of it as pressing the pause button 

- 📜 git stash list 

Shows a list of all your stashed changes 

Yes—you can stash more than once! 


- 🔁 git stash apply 

Reapplies the most recent stash (or a specific one), but keeps it in the stash list 

Great for reusing the same work across multiple branches 


- 🧹 git stash pop 

Reapplies the latest stash and removes it from the list after applying 

Ideal when you're done with that stash and want to keep things tidy 


🛠️ Real-World DevOps Example 

Let’s say: 

You’re editing a Terraform file on a feature branch 

Your teammate urgently needs you to hotfix something on main 

You haven’t committed your work yet 

✅ Use git stash 
🔁 Switch to main, fix the issue 
✅ Switch back to your branch 
📦 Use git stash pop to bring your changes back exactly where you left off 

 

💡 Why It’s So Useful 

Lets you switch context quickly without losing your work 

Avoids messy or rushed commits 

Keeps your Git history clean and intentional 

 

## ✅ Summary 

- git stash 

Saves all uncommitted changes temporarily 

- git stash list 

Lists all saved stashes 

- git stash apply 

Reapplies a stash without removing it from the list 

- git stash pop 

Reapplies a stash and removes it from the list 

🧠 Think of stash as a way to pause your work, help your team, and return without skipping a beat. 

## reset, revert, and cherry-pick 

In this lesson, we cover three powerful Git commands that can help you manage commits—or accidentally ruin things if used incorrectly. 

Let’s break them down clearly and safely: 

 

## 🔄 git revert – Safe Undo 

Creates a new commit that undoes the effect of a previous commit. 

Does not rewrite history, so it's safe to use on shared branches and in production environments. 

Ideal when you need to roll back a change without breaking anything for your team. 

💬 Example: 

git revert <commit-hash> 
 

🧠 Think of revert as: 

“Undo this change, but do it safely and visibly.” 

 

## 🔙 git reset – Powerful But Risky 

git reset moves your branch pointer backwards to an earlier commit. You can choose how much to keep or discard using different modes: 

🔹 --soft 

Moves the pointer back but keeps your changes staged. 

Use when you want to re-commit with different message or structure. 

 

- git reset --soft <commit-hash>
 

🔸 --mixed (default) 

Moves the pointer back and unstages the changes, but leaves them in your working directory.
 

🔥 --hard 

Moves the pointer back and deletes everything—staged, unstaged, and committed changes. 

Useful locally when you want a clean slate—but dangerous on shared branches. 

- git reset --hard <commit-hash> 
 

⚠️ Warning: Never use --hard reset on shared branches. It rewrites history and can break collaboration. 

🧠 Think of reset as: 

“Move back in time—but be very clear about what you’re willing to lose.” 

 

## 🍒 git cherry-pick – Pick a Commit Without Merging 

Lets you copy a single commit from another branch and apply it to your current one. 

Great for hotfixes or when you want only one change, not the entire branch. 

Doesn't bring the rest of the branch history—just that one commit. 

💬 Example: 

`git cherry-pick <commit-hash>` 
 

🧠 Think of cherry-pick as: 

“Take just this one change and apply it here.” 

 

✅ Summary 

Safe on Shared Branches? 
- git revert 

Undo a commit by adding a new "reversal" commit 

✅ Yes 

git reset --soft 

Rewind history but keep changes staged 

❌ Local use only 

git reset --mixed 

Rewind and unstage changes (default mode) 

❌ Local use only 

git reset --hard 

Rewind and delete changes completely 

❌ Danger: destructive 

git cherry-pick 

Apply a specific commit from another branch 

✅ Yes 

 

🧠 Final Tips 

Use revert for safe undos in shared/team environments. 

Use reset for local clean-ups, especially when experimenting. 

Use cherry-pick to copy one commit without merging a whole branch. 

Mastering these will level up your Git skills fast—especially in a DevOps environment where precision and version control are key. 

## Forks and Pull Requests 

When working on shared or open-source projects—especially ones you don’t directly control—you’ll often hear about forks and pull requests (PRs). These tools allow developers to collaborate safely and effectively. 

 

🍴 What is a Fork? 

A fork is your own personal copy of someone else’s repository. 

Commonly used in open-source projects or any project where you don’t have direct push access. 

When you fork a project on GitHub (or GitLab), a full copy is made under your GitHub username. 

From there, you can: 

- Clone the fork to your local machine 
- Make your changes 
- Push the changes back to your fork, not the original repo 
- Open a pull request to suggest those changes to the original project 

 

## 🔄 What is a Pull Request? 

A pull request (PR) is a way of saying: 

"Hey, I’ve made some changes—can you review and pull them into the main project?" 

Also called a merge request on GitLab (they’re the same concept). 

Used when you're proposing to merge one branch (usually from your fork) into another (usually the original project’s main branch). 

GitHub provides a user-friendly interface for pull requests: 

- The project owner can review your code 
- Comment or suggest changes 
- And finally, approve and merge if everything looks good 

 

🛡️ Why This Workflow Is Safe and Common 

When you fork a repo, you’re not changing the original (origin) repo directly. 

This keeps the project safe and stable while still allowing collaboration. 

Once your pull request is reviewed and accepted, your changes become part of the official project. 

 

🛠️ Real-World DevOps Example 

Let’s say you want to contribute a bug fix or feature to an open-source Terraform module: 

- Fork the module’s GitHub repo 
- Clone your fork locally 
- Create a new branch for your changes (e.g., fix-variable-naming) 
- Make your edits 
- Push the branch to your fork on GitHub 
- Open a pull request from your forked branch to the main project’s main branch 
- Wait for review and approval 

 

✅ Summary 

- Fork 

Your own copy of a repo – useful when you can’t push directly 

- Pull Request 

A formal proposal to merge your changes into the main project 

- Merge Request 

GitLab’s term for the same thing as a pull request 

🧠 Think of it like this: 

You fork a repo to experiment safely, and a pull request is how you ask to share your work with the original team. 

 

🔁 Two Common PR Patterns 

From a fork (most common in open source): 

- Fork → Edit → Branch → PR to main repo 

From the same repo (internal teams): 

- Create a new branch → Edit → PR to main branch 

Both are widely used, even within company teams and CI/CD workflows. 

Typical Git Workflow 

When working in a DevOps or software team, Git becomes part of your daily rhythm. This lesson walks through what a typical Git workflow looks like in the real world—used by teams everywhere, from open source to enterprise environments. 

 

🔁 Step-by-Step Git Workflow (Team-Based) 

 

1. 📥 Start with the Latest Code 

If it's your first time with the project, run: 

git clone <repo-url> 
 

If you've already cloned the repo, update your local copy: 

`git pull origin main`
 

✅ This ensures you’re working on the latest version of the code, avoiding conflicts later on. 

 

2. 🌱 Create a New Feature Branch 

Always work in a separate branch, not directly on main. 

Branch names usually describe the task you're working on: 

feature/login-page 

fix/missing-bug 

chore/update-docs 

💬 Example: 

`git switch -c feature/login-page` 
 

 

3. 🧑‍💻 Make and Save Your Changes 

Work locally: write code, edit configs, or tweak automation scripts. 

Use git add and git commit to track changes as you go: 

`git add .`
`git commit -m "Add login page layout"`

 

4. 🚀 Push Your Branch to GitHub 

Once ready to share your work with your team: 

git push origin feature/login-page 
 

 

5. 🔄 Open a Pull Request (PR) 

On GitHub, create a pull request (PR) from your branch to main. 

On GitLab, this is called a merge request (MR)—same idea. 

Tag teammates for review: request feedback or approval. 

 

6. 👀 Review, Comment, and Merge 

Your teammates may leave comments, request changes, or approve it. 

Once approved, the PR is merged into main. 

✅ Your changes are now part of the project! 

 

7. 🔄 Stay Up to Date 

While you're working, others are making changes too. 

It's good practice to regularly run: 

 

git pull --rebase origin main 
 

⚠️ This keeps your branch updated and avoids nasty merge conflicts later. 

 

🧠 Summary: The Standard Git Workflow 

Step 

Action 

Pull Latest 

git pull origin main or git clone 

Create Branch 

git switch -c feature/your-feature 

Make Changes 

git add → git commit 

Push to GitHub 

git push origin your-branch 

Open Pull Request 

Propose your changes for review 

Review and Merge 

Team checks, approves, and merges to main 

Rebase Regularly 

git pull --rebase origin main to stay in sync 

 

💬 Tip: This workflow is followed by 99% of real teams—get comfortable with it. Whether you're managing infrastructure as code (IaC), deploying via CI/CD, or collaborating on application code, this is how modern DevOps teams operate 

Lesson 22 – Trunk-Based Development 

You may hear the term Trunk-Based Development (TBD) mentioned often—especially in fast-paced engineering teams. While it sounds complex, the idea is actually quite simple. 

 

🌳 What is Trunk-Based Development? 

Trunk-Based Development means that developers work: 

Directly on the main branch 

Or on very short-lived branches that are merged back into main quickly (often within a few hours or a day) 

📌 In this workflow, main (sometimes called "trunk") is treated as the single source of truth, and it’s always kept in a working, deployable state. 

 

## ⚙️ Key Practices That Make This Safe 

To avoid chaos and broken builds, teams using Trunk-Based Development rely on: 

✅ 1. Strong CI Pipelines 

Every commit is automatically tested 

Ensures that only stable code is allowed into main 

🧪 2. Code Quality Checks 

Linting, static analysis, and peer reviews are built into the CI 

Prevents bugs and enforces best practices 

 

🌍 Who Uses This Workflow? 

Top tech companies like Google and Meta (Facebook) are known for using Trunk-Based Development. Why? 

It enables rapid releases 

Keeps teams aligned 

Encourages frequent collaboration 

 

⚠️ Pros and Considerations 

✅ Pros 

⚠️ Things to Consider 

- Fast delivery of features 
- Requires strong test coverage 
- Less chance of long-lived merge conflicts 
- Needs discipline around commit quality 
- More frequent feedback 
- May not suit teams without CI/CD setup 

 

🧠 Summary 

Trunk-Based Development = Short branches, fast merges, and automated testing. 

It’s ideal for DevOps teams that want to: 

Ship code often 

Reduce merge conflicts 

And move quickly without breaking production 