# Chapter 1: Introduction to Git

## Centralised vs Distributed Version Control

In the early days of version control, teams worked using a centralised system, where everyone relied on a single central server to manage code. This meant:

- If the central server went down, nobody could work—you couldn’t commit, update, or access code.  
- Developers had to manually communicate to avoid conflicts, saying things like “Don’t touch main.tf, I’m working on it.”  
- Teams often ended up in merge conflict wars, making collaboration slow and frustrating.

### Enter Git – A Distributed Solution

In 2005, after Linux kernel developers lost access to their existing version control tool, Linus Torvalds (creator of Linux) decided to build a better system. This led to the creation of Git.

Git introduced a distributed version control system (DVCS), meaning:

- Every developer has a full copy of the repository, including its entire history.  
- You can work offline, create branches freely, and merge changes when you're ready.  
- Git is faster, more reliable, and better suited for real-world collaboration—especially in DevOps environments.

### Simple Analogy

- Centralised Version Control (e.g., SVN): Like Google Docs—everyone edits one shared online file. If it's down, no one can access or save changes.  
- Distributed Version Control (Git): Like everyone having their own copy of the document. You work independently, then merge your updates later.

### Git as a Time Machine

Think of each Git commit as a save point or snapshot of your work:

- If you make a mistake, you can go back to a previous version.  
- This makes experimenting safer and collaboration smoother.

### Summary

Git didn’t just improve version control—it transformed how modern teams (especially in DevOps) collaborate at scale. By removing the bottlenecks of centralised systems, Git enables faster, safer, and more flexible development workflows.

---

## Git is Not a File Tracker

One of the first things to unlearn about Git is the idea that it’s simply a file tracker. It’s far more advanced than just recording what changed in a document line by line.

### Git Tracks Snapshots – Not Diffs

Every time you make a commit, Git captures a snapshot of what your project looks like at that moment.

- It doesn’t just track the difference (diff) between versions – it saves a full version of the files that changed.  
- If you only change one line, Git still stores a complete snapshot of that file—but it does so efficiently.

### How Git Works Internally

Git is built on a key-value store system using SHA-1 hashes:

- These are long, unique strings (e.g. `1a2b3c...`) that represent the exact content of a file.  
- If the content changes, the hash changes. If the content is the same, Git reuses the same object—regardless of the file name.

### Git Stores Everything as Objects

There are three main types of objects in Git:

- **Blobs** – Store the actual content of files.  
- **Trees** – Represent directories and how files are structured.  
- **Commits** – Point to a complete snapshot of your project, including metadata like author and message.

Git is content-addressed, meaning it focuses on what’s inside the file, not the file name itself. This approach helps Git stay accurate, efficient, and reliable.

### Why This Matters (Especially in DevOps)

This architecture makes Git incredibly fast and robust—especially when versioning large amounts of configuration files such as:

- Terraform files  
- Kubernetes manifests  
- Helm charts

Git can handle massive changes quickly, which is essential for modern DevOps workflows.

### Summary

Git isn’t just a tracker—it’s a smart, compressed, snapshot-based engine that uses hashing and content-based storage to manage your code. This design is why Git remains the go-to tool for version control in large, fast-paced engineering teams.
