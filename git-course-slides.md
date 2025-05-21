# Git Training Course
## Mastering Version Control

---

## Welcome!
### Course Objectives
- Understand Git fundamentals and internal mechanics
- Learn workflow strategies and when to use them
- Practice solving common Git problems
- Develop skills through hands-on exercises

---

## Part 1: Introduction to Git
### What is Version Control?

- **Definition:** System that records changes to files over time
- **Benefits:**
  - History tracking and documentation
  - Collaboration facilitation
  - Experimentation without risk
  - Accountability and governance

---

## Before Version Control

![Diagram: Multiple files named final.doc, final_v2.doc, final_FINAL.doc, etc.]

---

## With Version Control

![Diagram: Single repository with organised commit history]

---

## Version Control Evolution

- **First Generation:** Local VCS (RCS)
- **Second Generation:** Centralised VCS (CVS, Subversion)
- **Third Generation:** Distributed VCS (Git, Mercurial)

---

## What is Git?

- Created by Linus Torvalds in 2005 for Linux kernel development
- Distributed version control system
- Prioritises:
  - Speed
  - Data integrity
  - Distributed workflows
  - Branching capabilities

---

## Git vs. Other VCS

| Feature | Git | SVN | Mercurial |
|---------|-----|-----|-----------|
| Repository Model | Distributed | Centralised | Distributed |
| Branching | Lightweight | Heavy | Lightweight |
| Learning Curve | Steeper | Moderate | Moderate |
| Speed | Very Fast | Slower | Fast |
| Data Storage | Content-addressed | Delta-based | Hybrid |

---

## Key Git Terminology

- **Repository:** Project storage location
- **Commit:** Snapshot of changes
- **Branch:** Independent line of development
- **Staging Area:** Preparation space for commits
- **Remote:** External repository location
- **Clone:** Repository copy
- **Working Directory:** Current files you see and edit

---

## How Git Works Behind the Scenes

---

## Git's Object Model

![Diagram showing relationship between blobs, trees, and commits]

- **Blobs:** File contents
- **Trees:** Directory structures
- **Commits:** Snapshots with metadata
- **Tags:** Named references to specific commits

---

## SHA-1 Hashing

- Every object has a unique 40-character identifier
- Content-addressed storage system
- Example: `a1b2c3d4e5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t0`
- Guarantees data integrity
- Any change creates a completely new hash

---

## .git Directory Structure

```
.git/
├── HEAD          # Points to current branch
├── config        # Repository configuration
├── hooks/        # Event scripts
├── objects/      # All Git objects
├── refs/         # Branch pointers
└── index         # Staging area
```

---

## Git's Three-Tree Architecture

![Diagram showing working directory, staging area (index), and repository]

1. **Working Directory:** What you see and edit
2. **Staging Area:** Prepared changes
3. **Repository:** Committed history

---

## Criticisms of Git

- Steep learning curve
- Inconsistent command syntax
- Terminology confusion
- Complex error messages
- Command line focus (though improving)
- History rewriting capabilities (double-edged sword)

---

## Why Use Git Despite Challenges?

- Industry standard (ubiquitous)
- Powerful branching and merging
- Works offline
- Speed and efficiency
- Scale from solo to massive teams
- Rich ecosystem and tooling

---

## Part 2: Git Basics Practice

### Let's get hands-on!

---

## Basic Git Configuration

```bash
# Set your identity
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Set default editor
git config --global core.editor "code --wait"

# Configure line endings
git config --global core.autocrlf input  # Mac/Linux
git config --global core.autocrlf true   # Windows
```

---

## Creating a Repository

```bash
# Initialise a new repository
git init project-name

# Clone an existing repository
git clone https://github.com/username/repository.git
```

---

## Basic Git Workflow

![Diagram showing basic git workflow: edit → add → commit]

1. Modify files in working directory
2. Stage changes with `git add`
3. Commit changes with `git commit`
4. Repeat!

---

## Tracking Changes

```bash
# Check status
git status

# Stage changes
git add filename
git add .                  # Stage all changes

# Commit changes
git commit -m "Add feature X"
git commit -am "Fix bug Y"  # Stage tracked files and commit
```

---

## Viewing History

```bash
# View commit history
git log
git log --oneline
git log --graph --oneline --all
git show <commit-hash>
```

---

## Exercise: Your First Repository

1. Initialise a new repository
2. Create and stage files
3. Make commits with proper messages
4. View your commit history
5. Modify files and commit again

---

## Part 3: Git Workflow Strategies

---

## Trunk-Based Development

![Diagram showing trunk-based development with short-lived feature branches]

- Single mainline branch ("trunk" or "main")
- Short-lived feature branches
- Frequent integration
- Continuous delivery friendly

---

## Trunk-Based Development: Principles

- Keep branches small and short-lived (1-2 days)
- Merge frequently to trunk
- Deploy from trunk
- Use feature flags for incomplete features
- Automated testing crucial

---

## Trunk-Based Development: Pros & Cons

**Pros:**
- Reduces merge complexity
- Facilitates continuous integration
- Simpler workflow
- Less context switching

**Cons:**
- Requires disciplined developers
- Needs strong automated testing
- May be challenging for larger features
- Less formal release process

---

## Git Flow Strategy

![Diagram showing Git Flow with multiple branch types]

- Multiple long-lived branches
- Structured release process
- Formalised branch naming

---

## Git Flow Branch Types

- **main/master:** Production code
- **develop:** Integration branch
- **feature/\*:** New development
- **release/\*:** Release preparation
- **hotfix/\*:** Production fixes

---

## Git Flow Lifecycle

1. Feature developed on feature branch
2. Feature merged to develop
3. Release branch created from develop
4. Release branch merged to main and develop
5. Hotfixes applied directly to main and develop

---

## Git Flow: Pros & Cons

**Pros:**
- Clear separation of work
- Structured release process
- Good for versioned software
- Clear history visualisation

**Cons:**
- Complex with many branches
- Potential for long-lived branches
- Can encourage delayed integration
- Overhead for simpler projects

---

## Choosing the Right Workflow

- **Team Size:**
  - Smaller teams → Simpler workflows
  - Larger teams → More structure

- **Release Frequency:**
  - Continuous delivery → Trunk-based
  - Scheduled releases → Git Flow

- **Project Type:**
  - Web application → Trunk-based
  - Versioned product → Git Flow

---

## Workflow Decision Framework

| Factor | Trunk-Based Better | Git Flow Better |
|--------|-------------------|----------------|
| Release Frequency | Continuous | Scheduled |
| Team Experience | High Git proficiency | Mixed experience |
| Testing Maturity | Strong automation | Manual process |
| Project Type | Services/web apps | Versioned products |
| Team Size | Small-medium | Medium-large |

---

## Case Study Discussion

### 🎓 **Case Study: Predictive Maintenance for a Manufacturing Company**

#### **Project Background**

You're on a data science team at a mid-sized manufacturing firm. Your task is to build a predictive model to forecast equipment failures using sensor data. The goal is to deploy this as a web service for factory engineers.

#### **Project Team**

* 3 Data Scientists
* 1 ML Engineer
* 2 Backend Developers
* 1 DevOps Engineer

---

### 🚧 **Project Phases**

1. **Exploration & Prototyping**
2. **Model Development & Evaluation**
3. **Integration with Backend API**
4. **Deployment & Monitoring**
5. **Iterative Improvements**

---

### 🔁 Option 1: Trunk-Based Development

**You choose this strategy when:**

* Your team is small and collaborative.
* You deploy frequently (weekly or daily).
* You have a CI/CD pipeline and automated tests.
* You can communicate easily to avoid stepping on each other’s toes.

**How it looks:**

* Everyone commits to `main` or small feature branches merged rapidly.
* Code reviews are fast, testing is automated.
* Models and pipelines evolve incrementally.
* Experimentation is version-controlled but integrated continuously.

**Benefits:**

* Fast iteration on experiments and models.
* Minimal merge conflicts due to small diffs.
* Quick bug fixes and real-time collaboration.

**Challenges:**

* Requires strong test coverage.
* Needs discipline to keep the trunk healthy.
* Might be chaotic without good CI/CD and versioning strategies for models/data.

**When it works best:**

> During model development or when deploying fast, iterative improvements to the API.

---

### 🧭 Option 2: Git Flow

**You choose this strategy when:**

* Releases are scheduled and infrequent.
* You need multiple model versions in production.
* You have a QA phase before each release.
* You want a stable `main` branch always ready for production.

**How it looks:**

* Feature branches for model experiments.
* Develop branch for integration.
* Release branches to prep for QA.
* Hotfixes patched into `main` and merged back.

**Benefits:**

* Stability for production code.
* Controlled releases and traceability.
* Good for managing long-term experiments or model audits.

**Challenges:**

* More overhead, slower iteration.
* Merges are more complex.
* Requires team coordination and Git discipline.

**When it works best:**

> When maintaining a versioned model library or supporting regulated environments.

---

### 🧠 **Teaching Takeaway:**

Ask students to **analyze the trade-offs based on project goals**, such as:

* **Speed vs. Stability**
* **Experimentation vs. Governance**
* **Small teams vs. Large, distributed teams**

---

### 💬 Discussion Prompt:

> Suppose your predictive model needs to be updated monthly with new data and re-deployed. Would you prefer trunk-based development or git flow, and why?

Encourage students to consider:

* How often they'll release
* How they'll handle model versioning
* What the risks of bugs or bad models are

---

Would you like this packaged as a downloadable PDF or slide format for classroom use?


---

## Part 4: Collaborative Git Practice

### Let's try branching and merging!

---

## Creating and Managing Branches

```bash
# List branches
git branch

# Create a branch
git branch feature-login

# Switch to branch
git checkout feature-login
# OR (newer Git versions)
git switch feature-login

# Create and switch in one command
git checkout -b feature-login
git switch -c feature-login
```

---

## Merging Branches

```bash
# Switch to target branch
git checkout main

# Merge feature branch
git merge feature-login

# Delete branch after merging
git branch -d feature-login
```

---

## Merge Conflict Resolution

When Git can't automatically merge:

1. Git marks conflicts in files
2. Manually edit files to resolve
3. Stage resolved files (`git add`)
4. Complete merge (`git commit`)

---

## Exercise: Branching and Merging

1. Create a feature branch
2. Make changes on the feature branch
3. Switch back to main and make different changes
4. Merge the feature branch
5. Resolve any conflicts

---

## Part 5: Troubleshooting Common Git Problems

---

## Divergent Histories

![Diagram showing divergent branches]

- Local and remote histories have different commits
- Common when multiple developers work on same branch
- Occurs after pulling with local commits

---

## Resolving Divergent Histories

```bash
# Option 1: Merge remote changes (creates merge commit)
git pull

# Option 2: Rebase local changes on top of remote
git pull --rebase

# Option 3: Manual approach
git fetch
git rebase origin/main
# OR
git fetch
git merge origin/main
```

---

## Understanding Rebasing

![Diagram comparing merge vs rebase]

- **Merge:** Combines histories with merge commit
- **Rebase:** Replays your commits on top of another branch

---

## Rebasing Best Practices

- **Golden Rule:** Never rebase commits that have been pushed publicly
- Use for cleaning up local history before sharing
- Great for incorporating upstream changes
- Interactive rebasing for history cleanup

---

## Interactive Rebasing

```bash
# Interactive rebase of last 3 commits
git rebase -i HEAD~3
```

Commands:
- `pick`: Keep commit as is
- `reword`: Change commit message
- `edit`: Pause for amending
- `squash`: Combine with previous commit
- `fixup`: Combine and discard message
- `drop`: Remove commit

---

## Common Git Issues: Detached HEAD

```bash
# How you get there
git checkout a1b2c3d4  # Direct commit checkout

# How to recover
git branch temp-branch  # Create branch at current position
git checkout main       # Return to main branch
git merge temp-branch   # Bring changes into main
```

---

## Common Git Issues: Undoing Changes

```bash
# Unstage a file
git restore --staged file.txt

# Discard working directory changes
git restore file.txt

# Undo last commit (keep changes staged)
git reset --soft HEAD~1

# Undo last commit (discard changes)
git reset --hard HEAD~1

# Create new "undo" commit
git revert HEAD
```

---

## Common Git Issues: Stashing

```bash
# Save work in progress
git stash

# List stashes
git stash list

# Apply most recent stash
git stash apply

# Apply specific stash
git stash apply stash@{2}

# Apply and remove stash
git stash pop
```

---

## Exercise: Git Rescue Missions

1. Resolve a merge conflict
2. Recover from a detached HEAD
3. Stash changes and apply elsewhere
4. Fix a divergent history with rebase

---

## Part 6: Advanced Topics and Take-Home Exercises

---

## Advanced Git Concepts

- **Git Hooks:** Automated scripts triggered by Git events
- **Submodules:** Repositories within repositories
- **Git LFS:** Large File Storage for binary files
- **Bisect:** Binary search through history to find bugs
- **Worktrees:** Multiple working directories for one repo

---

## Take-Home Exercises

- **Basic:** Repository setup and branch management
- **Intermediate:** Collaborative workflows and time travel
- **Advanced:** Rebasing workshop and Git internals

*Detailed instructions in handout*

---

## Additional Resources

- [Official Git Documentation](https://git-scm.com/doc)
- [Pro Git Book](https://git-scm.com/book) (free online)
- [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
- [Learn Git Branching](https://learngitbranching.js.org/) (interactive tutorial)
- [Oh Shit, Git!?!](https://ohshitgit.com/) (practical recovery tips)

---

## Conclusion

- Git is powerful but requires practice
- Choose workflows that match your team and project
- Problem-solving skills come with experience
- Continue learning with take-home exercises

---

## Q&A

What questions do you have?
