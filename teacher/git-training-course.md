# Git Training Course: Mastering Version Control
## 3-Hour Lesson Plan

### Course Overview
This 3-hour training session introduces participants to Git version control system, covering fundamental concepts, workflow strategies, common problem-solving scenarios, and hands-on exercises.

### Learning Objectives
By the end of this training, participants will be able to:
- Understand the purpose and functionality of Git
- Set up and configure a Git repository
- Execute basic Git commands confidently
- Choose between workflow strategies (Trunk-Based vs. Git Flow)
- Troubleshoot common Git issues
- Apply Git best practices to their development workflow

### Materials Needed
- Computers with Git installed
- Visual presentation setup
- Prepared sample repositories for exercises
- Exercise worksheets
- Reference handouts

---

## Session Breakdown

### Part 1: Introduction to Git (45 minutes)

#### 1.1 What is Version Control? (10 minutes)
- **Lecture Content:**
  - Definition of version control
  - History of version control systems
  - Benefits of version control in software development
  - Types of version control systems (centralized vs. distributed)

- **Interactive Activity:**
  - Group discussion: "Pain points without version control"
  - Quick poll: Previous experience with version control systems

#### 1.2 What is Git? (10 minutes)
- **Lecture Content:**
  - History and creation by Linus Torvalds
  - Core philosophy of Git
  - Git vs. other version control systems
  - Key terminology: repository, commit, branch, etc.

- **Visual Aids:**
  - Timeline of Git's development
  - Comparison chart with other VCS

#### 1.3 How Git Works Behind the Scenes (15 minutes)
- **Lecture Content:**
  - Git's object model (blobs, trees, commits)
  - SHA-1 hashing and content addressing
  - The .git directory structure
  - How Git tracks changes

- **Demonstration:**
  - Exploration of .git directory
  - Visual representation of Git's data model

#### 1.4 Criticisms and Challenges of Git (5 minutes)
- **Lecture Content:**
  - Learning curve steepness
  - Terminology inconsistencies
  - Command complexity
  - Common misconceptions

- **Interactive Activity:**
  - Quick brainstorm: "What aspects of Git confuse you?"

#### 1.5 Why Use Git? (5 minutes)
- **Lecture Content:**
  - Distributed development benefits
  - History preservation
  - Collaborative advantages
  - Industry standard status

- **Case Study:**
  - Brief examples of Git usage in prominent projects

### Part 2: Git Basics Practice (30 minutes)

#### 2.1 Hands-on Exercise: Git Setup and First Commits
- **Activities:**
  - Installing and configuring Git (if needed)
  - Creating a new repository
  - Making initial commits
  - Viewing commit history
  - Understanding the staging area

- **Commands Covered:**
  - `git init`
  - `git config`
  - `git add`
  - `git commit`
  - `git status`
  - `git log`

### Part 3: Git Workflow Strategies (40 minutes)

#### 3.1 Trunk-Based Development (15 minutes)
- **Lecture Content:**
  - Principles of trunk-based development
  - Single mainline branch philosophy
  - Short-lived feature branches
  - Continuous integration focus

- **Visual Aids:**
  - Trunk-based workflow diagram
  - Example commit history visualization

#### 3.2 Git Flow Strategy (15 minutes)
- **Lecture Content:**
  - Multiple long-lived branches
  - Feature/release/hotfix branch structures
  - Branch naming conventions
  - Release management approach

- **Visual Aids:**
  - Git Flow diagram
  - Branch lifecycle visualization

#### 3.3 Choosing the Right Workflow (10 minutes)
- **Lecture Content:**
  - Team size considerations
  - Project complexity factors
  - Release frequency impact
  - Team experience level

- **Interactive Activity:**
  - Case study analysis: "Which workflow for this scenario?"
  - Small group discussions on workflow preferences

### Break (10 minutes)

### Part 4: Collaborative Git Practice (30 minutes)

#### 4.1 Hands-on Exercise: Branching and Merging
- **Activities:**
  - Creating branches
  - Switching between branches
  - Making changes on branches
  - Merging branches
  - Resolving simple merge conflicts

- **Commands Covered:**
  - `git branch`
  - `git checkout` / `git switch`
  - `git merge`
  - Conflict resolution process

### Part 5: Troubleshooting Common Git Problems (35 minutes)

#### 5.1 Divergent Histories (10 minutes)
- **Lecture Content:**
  - Why histories diverge
  - Local vs. remote tracking
  - Visualization of divergent branches

- **Demonstration:**
  - Creating a divergent history scenario
  - Resolving with various approaches

#### 5.2 Rebasing Scenarios (10 minutes)
- **Lecture Content:**
  - Rebasing vs. merging
  - When to use rebasing
  - Rebasing dangers and golden rule

- **Demonstration:**
  - Interactive rebasing process
  - Handling rebasing conflicts

#### 5.3 Other Common Issues (15 minutes)
- **Lecture Content:**
  - Detached HEAD state
  - Undoing commits and changes
  - Stashing work in progress
  - Cherry picking

- **Hands-on Exercise:**
  - "Git Rescue Missions" - solving prepared problem scenarios

- **Commands Covered:**
  - `git rebase`
  - `git reset`
  - `git revert`
  - `git stash`
  - `git cherry-pick`
  - `git reflog`

### Part 6: Advanced Topics and Take-Home Exercises (20 minutes)

#### 6.1 Introduction to Advanced Concepts
- **Brief Overview:**
  - Git hooks
  - Submodules
  - Git LFS (Large File Storage)
  - Bisect for debugging

#### 6.2 Take-Home Exercises Distribution
- **Exercise Sets:**
  - Basic skill reinforcement exercises
  - Intermediate workflow challenges
  - Advanced problem-solving scenarios
  - Real-world simulation project

#### 6.3 Additional Resources
- **Resource List:**
  - Official documentation
  - Interactive learning tools
  - Recommended books and tutorials
  - Cheat sheets and quick references

### Conclusion and Q&A (10 minutes)
- Recap of key concepts
- Addressing remaining questions
- Course feedback collection
- Next steps for continued learning

---

## Take-Home Exercises

### Basic Exercises
1. **Repository Exploration**
   - Create a new repository
   - Add files with different extensions
   - Create a .gitignore file
   - Make commits with proper messages
   - View and interpret the commit history

2. **Branching Practice**
   - Create multiple branches for different features
   - Make changes across branches
   - Merge branches in different orders
   - Observe how merge history appears

### Intermediate Exercises
1. **Collaborative Simulation**
   - Clone a provided repository
   - Create a feature branch
   - Submit changes via pull request (if using GitHub/GitLab)
   - Review another participant's changes
   - Handle merge conflicts

2. **Time Travel Exercise**
   - Explore previous versions of code
   - Restore deleted files from history
   - Create a branch from a previous commit
   - Use bisect to find a "broken" commit

### Advanced Exercises
1. **Rebase Workshop**
   - Practice interactive rebasing
   - Squash related commits
   - Rewrite commit history
   - Force push safely to a personal branch

2. **Git Internals Project**
   - Manually inspect objects in .git/objects
   - Create a commit without standard commands
   - Use low-level Git plumbing commands
   - Map the object relationships in a commit

3. **Workflow Implementation**
   - Implement either Git Flow or Trunk-Based development
   - Document the process and decision points
   - Simulate a complete release cycle
   - Evaluate the pros and cons experienced

---

## Slide Suggestions

### Introduction Section
- **Slide 1:** Title slide with course name and instructor
- **Slide 2:** Agenda and learning objectives
- **Slide 3:** What is version control? (with before/after illustrations)
- **Slide 4:** History of version control systems (timeline)
- **Slide 5:** Git origin story (with Linus Torvalds photo)
- **Slide 6:** Distributed vs. Centralized VCS (comparison diagram)
- **Slide 7:** Key Git terminology (visual glossary)

### Git Internals Section
- **Slide 8:** Git's object model (diagram showing blobs, trees, commits)
- **Slide 9:** SHA-1 hashing visualization
- **Slide 10:** The .git directory structure (tree view)
- **Slide 11:** How changes are tracked (visual diff)
- **Slide 12:** Git's staging area explained (three-tree architecture)

### Workflow Strategies Section
- **Slide 13:** Trunk-Based Development overview (visual diagram)
- **Slide 14:** Git Flow model (comprehensive branch diagram)
- **Slide 15:** Workflow comparison chart (pros and cons table)
- **Slide 16:** Decision framework for choosing a workflow
- **Slide 17:** Real-world examples of each workflow

### Troubleshooting Section
- **Slide 18:** Common Git error messages decoded
- **Slide 19:** Divergent histories visualization
- **Slide 20:** Rebasing illustrated (before/after diagrams)
- **Slide 21:** Merge conflict resolution walkthrough
- **Slide 22:** Git recovery tools and techniques

### Reference Slides
- **Slide 23:** Essential Git commands cheat sheet
- **Slide 24:** Recommended Git configuration settings
- **Slide 25:** Additional resources and learning materials
- **Slide 26:** Contact information and Q&A prompt

---

## Course Handouts

### Recommended Handout Materials
1. **Command Reference Sheet**
   - Categorized by function (basic, branch management, remote operations)
   - Common flags and options
   - Example usage

2. **Workflow Decision Tree**
   - Questionnaire to determine optimal workflow
   - Visual decision paths
   - Pros and cons summary

3. **Troubleshooting Guide**
   - Common error messages
   - Diagnostic steps
   - Resolution approaches

4. **Exercise Worksheets**
   - Step-by-step instructions
   - Challenge questions
   - Blank spaces for notes and observations

---

## Instructor Notes

### Pre-Session Preparation
- Ensure all participants have Git installed
- Prepare sample repositories for exercises
- Test all demonstrations on the presentation environment
- Review common issues specific to participants' development environments

### Session Delivery Tips
- Begin with a quick assessment of participant experience levels
- Adjust pace based on group comprehension
- Emphasize practical application over theory
- Use real-world analogies for abstract concepts
- Allow extra time for troubleshooting during exercises
- Capture questions that require follow-up research

### Common Sticking Points
- Conceptual understanding of staging area
- Distinguishing between local and remote operations
- Visualization of branching strategies
- Rebasing concepts and conflicts
- Recovering from detached HEAD states

### Post-Session Follow-up
- Provide access to recorded session if possible
- Share links to demonstrated examples
- Create forum or communication channel for questions
- Schedule optional follow-up session for advanced topics
