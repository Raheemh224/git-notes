### Chapter 5 – Git Best Practices 

##  Commit Hygiene and Best Practices 

Maintaining good commit hygiene is essential to keeping your Git history clean, readable, and helpful — especially as your codebase and team grow. Below are a few key best practices to follow: 

 

## 📝 1. Write Clear and Descriptive Commit Messages 

Avoid vague messages like update stuff, final fix, or last changes. Instead, your commit message should clearly describe what was changed and why. 

Examples of good commit messages: 

- Fix navbar logo alignment on mobile view 
- Add authentication middleware to user routes 
- Refactor signup form validation logic 

These kinds of messages help your teammates (and future you) quickly understand the purpose of each change. 

 

## 🔀 2. Squash Commits Before Merging 

When working on a feature branch, it’s common to have multiple work-in-progress (WIP) commits like: 

- fix typo 
- test login again 
- debugging issue 
- finally fixed 

Before merging your pull request, squash these into a single, meaningful commit. This keeps the main branch history clean and avoids clutter. 

✅ Clean history = easier debugging and code review. 

 

## 🔄 3. One Logical Change per Commit 

Each commit should represent one isolated, logical change. For example, if you're fixing a bug and updating the README, these should be two separate commits. 

Why? 

- Easier to roll back specific changes 
- Easier to track down bugs 
- Better collaboration and code reviews 

 

## 🚫 4. Avoid Noisy or Confusing Commit History 

Try to avoid: 

- Repetitive commits like fix, fix again, final final fix 
- Messy merges like merge branch main into main, main into dev final, etc. 

Take a moment to name branches properly and structure your commits cleanly. A little extra care now saves a lot of confusion later. 

## Pre-commit and automation 

Before you hit git commit, it’s worth asking: 

❓ Is my code clean, secure, and working properly? 

That’s exactly what pre-commit hooks and automation tools are designed to help with. 

 

🔐 Why Pre-Commit Checks Matter 

In a collaborative DevOps environment, bad code can mean: 

- Broken builds 
- Leaked secrets 
- Inconsistent formatting 
- Wasted time fixing silly mistakes 

Pre-commit tools act as a first line of defence, stopping issues before they ever reach the repository. 

 

⚙️ How It Works 

You write your code. 

You save your file. 

You run: 

`git add .`
`git commit -m "Add feature"` 
 

Pre-commit hooks run automatically, checking your code before the commit is accepted. 

If anything fails (e.g. a linter error or a leaked secret), the commit is blocked until it’s resolved. 

 

🛠️ Popular Pre-Commit Tools (DevOps & Beyond) 

- pre-commit 
Framework for managing Git hooks (language-agnostic) 

- Husky 
Great for JavaScript/Node.js projects 

- tflint / tfsec 
Scan Terraform for issues & security flaws 

- detect-secrets 
Checks for API keys or secrets 

- Black / Flake8 
Python formatting and linting 

These tools are easy to integrate and run either: 

- Locally, before each commit 
- Or in CI/CD pipelines (for automated checks on push) 

 

## 🧪 Combine with CI/CD Pipelines 

Once you’ve added pre-commit checks locally, you can also integrate them into your CI pipelines (covered in the CI/CD module). 

This means: 

Consistent quality across local and cloud environments 

Failing commits are caught automatically, even if someone skips local checks 

 

## ✅ Benefits of Using Pre-Commit & Automation 

- Catches bugs and issues early 
- Saves time during code reviews 
- Keeps your pull requests clean and professional 
- Improves teamwide consistency without manual policing 
- Makes you look sharp and reliable as a DevOps engineer 

## Common Git Mistakes (Real-World Scenarios) 

Even experienced developers make mistakes with Git – it's completely normal, especially early on. Below are some of the most common pitfalls, along with tips to avoid them. These are drawn directly from real-world DevOps teams and workflows. 

 

🔁 1. Forgetting to Pull Before Pushing 

Mistake: Making changes locally and running git push without first pulling from the remote. 

Git will reject the push if someone else has already pushed changes before you. 

This happens a lot in team settings. 

✅ Tip: 
 Always run: 

`git pull --rebase`
 

before starting work or before pushing changes. This keeps your history tidy and reduces merge conflicts. 

 

🧨 2. Force Pushing to Shared Branches (like main) 

Mistake: Running git push --force on branches used by the whole team. 

This can wipe out teammates’ commits, undoing their work without warning. 

✅ Tip: 

Avoid force pushing to shared branches entirely. 

If absolutely necessary, use: 

`git push --force-with-lease` 
 

…but even then, communicate with your team first. 

 

🔐 3. Accidentally Committing Secrets (AWS Keys, API Tokens, etc.) 

Mistake: Pushing sensitive data like .env files, private keys, or credentials to GitHub. 

Hackers run bots that scan GitHub in real-time looking for leaked secrets. 

These can be exploited within minutes. 

✅ Tip: 

Use tools like git-secrets, truffleHog, or pre-commit hooks to catch secrets before they’re committed. 

Add sensitive files to your .gitignore. 

 

🧐 4. Merging Without Code Review 

Mistake: Merging your branch without reviewing the code (even if you're the only person on the team). 

Skipping reviews can lead to bugs or accidental changes going unnoticed. 

✅ Tip: 

Always review your code before merging. 

Use pull requests as a moment to pause and confirm: 

“Is this what I meant to do?” 

“Is this production-safe?” 

 

📁 5. Committing Large or Unnecessary Files 

Mistake: Adding things like: 

node_modules/ 

.DS_Store 

Large binaries or temp files 

Secret .env files 

✅ Tip: 
 Use a .gitignore file to keep your repo clean. Example: 

gitignore 

node_modules/ 
.env 
.DS_Store 
*.log 
 

Learn what files should be excluded from version control and treat .gitignore as a vital part of every project. 

## Git at Scale 

As teams and codebases grow, Git usage needs to scale with it. The same Git fundamentals apply, but workflows and tools evolve. Here’s how large organisations like Google, Meta, and Uber use Git efficiently at scale. 

 

1. 🧱 Monorepos 

A monorepo is a single Git repository that contains multiple projects or services (instead of one repo per service). 

✅ Pros: 

Easier to manage shared dependencies and tooling. 

Centralised versioning and history. 

⚠️ Cons: 

CI pipelines can become very slow unless optimised. 

🛠️ Large teams often use tools like: 

Nx, Turborepo, Bazel 

These tools support selective builds (only test/build what changed). 

 

2. 🧳 Sparse Checkout 

This lets you clone only part of a large repo (e.g. one folder), which is useful if the full repo is massive. 

✅ Saves bandwidth and local storage. 

 

`git sparse-checkout init --cone`
`git sparse-checkout set path/to/folder` 
 

 

3. 🧬 Git LFS (Large File Storage) 

Git isn’t designed for storing large binary files (e.g. images, videos, datasets). That’s where Git LFS comes in. 

🔁 It replaces large files with lightweight pointers and downloads the real content separately. 

`git lfs install`
`git lfs track "*.mp4"` 
 

 

4. 🧹 Cleaning Old Repos (e.g. removing secrets or folders) 

If your repo has been around "since the dinosaurs", it might have old secrets or folders in its history. 

✅ Use tools like: 

git filter-repo (modern, safer alternative to filter-branch) 

Strip secrets, sensitive data, or entire directories from commit history 

 

5. 🔗 Submodules vs Subtrees 

These are ways to manage multiple Git repos under one main repo. 

Submodules: Reference another Git repo. Fragile and harder to work with. 

Subtrees: More native to Git. Easier to manage and merge. 

💡 If you don’t need to keep separate Git histories, subtrees are often the better choice. 

 

6. 🔐 Enforcing Standards at Scale 

At scale, you don’t rely on good habits alone. You enforce quality and security using: 

Pre-commit hooks (e.g. pre-commit, Husky) 

Server-side hooks 

Bots for: 

Security scanning (e.g. GitHub Dependabot) 

Commit message linting 

Pull request enforcement 

 

7. ☁️ GitOps – Git for Infrastructure 

Git isn't just for app code anymore. 

Tools like Argo CD and Flux watch Git repos for infrastructure changes and apply them automatically to your Kubernetes clusters. 

✅ This makes Git your single source of truth for infrastructure. 
 

🧩 Final Thought 

Git scales well – but your workflow must mature. 
 Same Git. Smarter usage. 

Git ammend 

 

 