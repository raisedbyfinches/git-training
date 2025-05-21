# Git Training Course: Instructor Guide

This guide provides detailed instructions for teaching, including teaching tips, common questions, and preparation guidance.

## Pre-Course Preparation

### Technical Setup

1. **Environment preparation:**
   - Ensure Git is installed on your demonstration computer (version 2.30+ recommended)
   - Configure Git with your demonstration details
   - Have sample repositories prepared for exercises
   - Test all commands in your specific environment
   - Prepare fallback options for potential technical issues

2. **Create example repositories:**
   - A clean repository for basic demonstrations
   - A repository with multiple branches for workflow demonstrations
   - A repository with deliberate problems for troubleshooting exercises
   - A repository with complex history for visualisation

3. **Classroom setup:**
   - Request participants install Git before the session if not working in Data Workspace
   - Prepare a troubleshooting guide for installation issues
   - Test classroom projector/screen with Git GUI tools

### Content Preparation

1. **Customise examples:**
   - Adjust examples to match participants' domain/industry
   - Consider the programming languages used by participants
   - Modify workflow examples to match company practices

2. **Prepare visual aids:**
   - Print larger versions of key diagrams
   - Create handouts for reference during exercises
   - Prepare alternative explanation approaches for complex concepts

3. **Know your audience:**
   - Survey participants' Git experience before the session
   - Identify specific pain points they want to address
   - Understand the workflow currently used in their teams

## Teaching Approach

### General Teaching Tips

1. **Engagement strategies:**
   - Begin with a quick survey of participant experience
   - Use real-world analogies for abstract Git concepts
   - Incorporate short group discussions (2-3 minutes)
   - Encourage questions throughout rather than just at the end

2. **Demonstration techniques:**
   - Use large, readable font in terminal windows
   - Explain commands before typing them
   - Show command results and explain their meaning
   - Demonstrate common errors and recovery techniques

3. **Pacing guidance:**
   - Allow extra time for exercise troubleshooting
   - Build in flexible segments that can be expanded or contracted
   - Have advanced material ready for groups that progress quickly
   - Keep a countdown timer visible during exercises

### Explaining Difficult Concepts

1. **Git's object model:**
   - Use the "shopping bag" analogy: commits are shopping bags that contain file snapshots and metadata
   - Draw diagrams showing the relationships between blobs, trees, commits
   - Show actual object contents with `git cat-file`
   - Build the concept step-by-step with a small repository example

2. **Rebasing:**
   - Start with the "replay" metaphor: rebasing is replaying your changes on a new base
   - Contrast with merging using railroad track diagrams
   - Show a live demonstration with visible history changes
   - Emphasize the "golden rule" about not rebasing public history

3. **Detached HEAD:**
   - Use the "bookmark" analogy: branches are bookmarks, detached HEAD is reading without a bookmark
   - Draw memory models showing references
   - Demonstrate creating and losing work in detached HEAD
   - Show recovery techniques step by step

4. **Index/staging area:**
   - Use the "packing a suitcase" analogy: you decide what goes in before finalizing
   - Show partial staging of files and hunks
   - Demonstrate how the index enables atomic commits
   - Build the three-tree model (working directory, index, repository)

## Section-by-Section Guidance

### Part 1: Introduction to Git

**Key teaching points:**
- Emphasize the distributed nature as Git's key innovation
- Connect version control benefits to participants' daily work
- Address common misconceptions about Git vs. GitHub
- Build a logical progression from problem (no version control) to solution (Git)

**Potential questions and answers:**

Q: "Why is Git better than older systems like SVN?"
A: "Git's distributed nature means every clone is a full backup, it works offline, offers faster operations, and has superior branching capabilities. However, it does have a steeper learning curve."

Q: "Do I need GitHub to use Git?"
A: "No, Git is a standalone tool. GitHub is a service that hosts Git repositories and adds collaboration features. You can use Git locally or with any Git hosting service like GitLab, Bitbucket, or your own server."

Q: "Why does Git seem so complicated?"
A: "Git was designed by kernel developers for kernel developers, prioritizing power and flexibility over ease of use. Its terminology can be confusing, but once you understand the core concepts, it becomes more intuitive. We'll focus on building that foundation today."

### Part 2: Git Basics Practice

**Key teaching points:**
- Emphasize muscle memory through repetition of basic commands
- Connect commands to the conceptual model established earlier
- Show command variations to accommodate different preferences
- Highlight common pitfalls and how to avoid them

**Demonstration script:**

1. Initialize repository:
   ```bash
   mkdir demo-project
   cd demo-project
   git init
   ls -la  # Show .git directory
   ```
   *Explain*: "This creates a new Git repository. The .git directory contains everything Git needs to track your project."

2. Configure Git:
   ```bash
   git config --local user.name "Demo User"
   git config --local user.email "demo@example.com"
   git config --list
   ```
   *Explain*: "Git needs to know who's making changes. This information is stored with every commit."

3. Make first changes:
   ```bash
   echo "# Demo Project" > README.md
   git status  # Show untracked file
   ```
   *Explain*: "Git has noticed our new file but isn't tracking it yet. Let's add it."

4. Stage and commit:
   ```bash
   git add README.md
   git status  # Show staged file
   git commit -m "Add README file"
   ```
   *Explain*: "We've now recorded our first snapshot in Git's history."

5. View history:
   ```bash
   git log
   git log --oneline
   ```
   *Explain*: "This shows the history of our repository. Each commit has a unique identifier."

**Common pitfalls to highlight:**
- Not setting user name/email (commits fail or use system defaults)
- Forgetting to add files before committing
- Writing uninformative commit messages
- Not checking status before operations

### Part 3: Git Workflow Strategies

**Key teaching points:**
- Present workflows as tools, not dogma
- Connect workflow choices to business and team contexts
- Use visual diagrams to illustrate workflow patterns
- Show concrete examples of each workflow in action

**Discussion prompts:**
- "What are your current release cycles and how might they influence workflow choice?"
- "How large is your development team and how is it structured?"
- "What problems have you encountered with your current branching strategy?"

**Workflow comparison table (for whiteboard):**

| Aspect | Trunk-Based | Git Flow |
|--------|-------------|----------|
| Branch Lifespan | Short (hours/days) | Long (days/weeks) |
| Release Cadence | Continuous | Scheduled |
| Complexity | Lower | Higher |
| Team Size | Any (scales well) | Medium to large |
| Code Review | Pull requests or pair | Pull requests |
| Integration | Continuous | Batch |
| Risk Profile | Small, frequent risks | Larger, less frequent |
| Testing Needs | Strong automation | Manual acceptable |

### Part 4: Collaborative Git Practice

**Key teaching points:**
- Emphasize communication aspects of collaboration
- Demonstrate a complete collaborative cycle
- Show conflict resolution techniques step by step
- Discuss team conventions and standards

**Conflict resolution walkthrough:**

1. Set up the conflict:
   ```bash
   # Developer 1
   git checkout -b feature-A
   echo "Line added by Developer 1" >> shared.txt
   git add shared.txt
   git commit -m "Developer 1 changes"
   
   # Developer 2
   git checkout main
   git checkout -b feature-B
   echo "Different line added by Developer 2" >> shared.txt
   git add shared.txt
   git commit -m "Developer 2 changes"
   
   # Merge attempt
   git checkout main
   git merge feature-A  # Succeeds
   git merge feature-B  # Conflict!
   ```

2. Show the conflict:
   ```bash
   git status
   cat shared.txt  # Show conflict markers
   ```
   *Explain*: "Git couldn't automatically determine which changes to keep, so it marks the conflicts and asks us to resolve them."

3. Resolve manually:
   ```bash
   # Edit the file to resolve
   vim shared.txt  # Remove markers, keep both lines
   
   git add shared.txt
   git status
   git commit  # Finalize merge
   ```
   *Explain*: "After editing the file to our satisfaction, we tell Git the conflict is resolved by adding it, then complete the merge."

4. Show alternate tools:
   ```bash
   git mergetool  # If configured
   ```
   *Explain*: "There are graphical tools that can make conflict resolution easier."

### Part 5: Troubleshooting Common Git Problems

**Key teaching points:**
- Frame problems as common, not user failures
- Demonstrate diagnostic approaches, not just solutions
- Teach the "why" behind issues to build deeper understanding
- Show multiple solution paths where applicable

**Demonstration script for divergent histories:**

1. Create the scenario:
   ```bash
   # Create divergent history
   git checkout main
   echo "Remote change" > remote-change.txt
   git add remote-change.txt
   git commit -m "Change on remote"
   
   git checkout -b local-branch HEAD~1
   echo "Local change" > local-change.txt
   git add local-change.txt
   git commit -m "Local change"
   ```

2. Explain the problem:
   ```bash
   git checkout main
   git log --oneline
   git checkout local-branch
   git log --oneline
   ```
   *Explain*: "Our local branch is now behind main but also has unique commits. This commonly happens when others push to the same branch you're working on."

3. Solution approach 1: Merge
   ```bash
   git checkout local-branch
   git merge main
   git log --graph --oneline --all
   ```
   *Explain*: "Merging creates a new commit that combines the histories. This preserves the exact history but adds an extra commit."

4. Reset and show solution approach 2: Rebase
   ```bash
   # Reset to recreate the scenario
   git checkout local-branch
   git reset --hard HEAD~1
   echo "Local change" > local-change.txt
   git add local-change.txt
   git commit -m "Local change"
   
   # Rebase approach
   git rebase main
   git log --graph --oneline --all
   ```
   *Explain*: "Rebasing replays your changes on top of the updated main branch. This creates a linear history but changes your commit hashes."

5. Discuss when to use each approach:
   *Explain*: "Merge when working on a feature branch that others use. Rebase when catching up your feature branch before merging to keep history clean. Never rebase shared branches."

### Part 6: Advanced Topics and Take-Home Exercises

**Key teaching points:**
- Preview advanced concepts to spark continued learning
- Connect take-home exercises to real-world applications
- Provide clear paths for further skill development
- Emphasize Git as a career-long learning journey

**Exercise preview approach:**
1. Briefly demonstrate one advanced concept (e.g., bisect)
2. Show a practical application scenario
3. Connect to the provided take-home exercise
4. Provide resources for self-guided learning

## Assessment Strategies

### Evaluating Participant Progress

1. **Observation during exercises:**
   - Watch for command hesitation
   - Note questions asked during practice
   - Check completed exercise outcomes
   - Listen for conceptual misunderstandings

2. **Quick knowledge checks:**
   - "What's the difference between `git add` and `git commit`?"
   - "What happens when we create a branch?"
   - "How does Git know if a file has changed?"
   - "What distinguishes Trunk-Based from Git Flow?"

3. **Exercise outcomes:**
   - Clean commit history
   - Successful branch merges
   - Correct problem resolution
   - Appropriate workflow implementation

### Follow-up Assessment

1. **Post-course survey:**
   - Self-assessment of comfort with Git commands
   - Specific concepts still needing clarification
   - Workflow implementation plans
   - Additional Git topics of interest

2. **Two-week follow-up:**
   - Quick survey on Git usage since training
   - Common issues encountered
   - Successful techniques applied
   - Additional learning needs identified

## Common Issues and Solutions

### Technical Problems

1. **Git installation issues:**
   - Windows: Ensure Git Bash is installed
   - Mac: Check if Xcode Command Line Tools are installed
   - Linux: Verify package manager installation worked
   - Solution: Have USB drives with installers ready

2. **Configuration problems:**
   - Issue: Commands fail due to incomplete configuration
   - Solution: Review `git config --list` output
   - Ensure user.name and user.email are set

3. **Permission errors:**
   - Issue: Cannot create/modify files in repository
   - Solution: Check file system permissions
   - For shared repositories, review shared ownership

4. **Proxy/network issues:**
   - Issue: Remote operations fail
   - Solution: Configure Git proxy settings
   - Test with `git ls-remote` to isolate network problems

### Conceptual Misunderstandings

1. **Confusing staging area:**
   - Symptom: Changes not appearing in commits
   - Reinforcement: Repeat "edit → add → commit" cycle
   - Visual: Draw the three-tree model again

2. **Branch confusion:**
   - Symptom: Uncertainty about current branch
   - Reinforcement: Always check `git status` before operations
   - Demonstration: Show branch switching effects on files

3. **Merge vs. rebase:**
   - Symptom: Inappropriate usage choices
   - Reinforcement: Golden rule - "Never rebase public history"
   - Visual: Draw both operations again side by side

4. **Remote tracking misunderstandings:**
   - Symptom: Confusion between local and remote branches
   - Reinforcement: Explain remote references as "bookmarks"
   - Demonstration: Show `git remote -v` and `git branch -vv`

## Adapting to Different Audiences

### For Complete Beginners

- Reduce content to focus on core commands
- Add more repetitive practice exercises
- Use stronger analogies for abstract concepts
- Provide command reference sheets
- Slow down demonstrations
- Increase guided practice time

### For Mixed Experience Groups

- Employ peer coaching during exercises
- Prepare extension tasks for advanced users
- Use quick "pretest" to identify experience levels
- Create mixed-skill breakout groups
- Offer optional "catch-up" materials

### For Advanced Users

- Focus more on workflows and best practices
- Expand troubleshooting scenarios
- Dive deeper into Git internals
- Discuss Git scripting and automation
- Cover advanced topics like submodules, filters, hooks
- Facilitate experience sharing among participants

## Post-Course Support

### Reference Materials

1. **Essential handouts:**
   - Command cheat sheet with examples
   - Workflow decision tree
   - Common error message guide
   - Recommended Git configuration settings

2. **Digital resources:**
   - Course slides and notes
   - Exercise repositories
   - Script templates for common operations
   - Recommended external learning resources

### Follow-up Support

1. **Support channels:**
   - Dedicated Slack/Teams channel
   - Follow-up Q&A session (2 weeks after)
   - Email support for specific questions
   - Peer knowledge sharing forum

2. **Additional training opportunities:**
   - Advanced Git techniques workshop
   - CI/CD with Git integration session
   - Git for specific roles (designer, PM, etc.)
   - Custom workflow implementation coaching

## Appendix: Analogies for Git Concepts

Using effective analogies can significantly improve understanding of Git's abstract concepts.

### Core Concept Analogies

1. **Repository:**
   - "A repository is like a project folder that remembers everything that ever happened to its contents."
   - "Think of it as a magic filing cabinet that records every version of every document."

2. **Commits:**
   - "Commits are like taking a snapshot of your entire project at a moment in time."
   - "Each commit is like saving a game - creating a point you can return to."

3. **Branches:**
   - "Branches are like parallel universes where you can try different ideas."
   - "Think of branches as different drafts of the same document, each exploring different approaches."

4. **Staging area:**
   - "The staging area is like a packing area where you decide what to include in your next shipment (commit)."
   - "It's like a shopping cart - you can add and remove items before checking out (committing)."

5. **Merging:**
   - "Merging is like combining two recipe variants into one master recipe."
   - "It's similar to two tributaries joining into one larger river."

6. **Rebasing:**
   - "Rebasing is like carefully moving your house onto a new foundation."
   - "It's like rewriting history to make it appear that you built on the latest version all along."

7. **Remote repository:**
   - "A remote is like a backup copy of your project on another computer, with added collaboration features."
   - "Think of it as the official copy of a document that everyone syncs with."

### Workflow Analogies

1. **Trunk-Based Development:**
   - "Trunk-based is like a high-frequency train service - small batches departing frequently."
   - "It's similar to continuous assembly rather than batch manufacturing."

2. **Git Flow:**
   - "Git Flow is like a publishing process with drafts, editing, and formal publication stages."
   - "It's similar to how films are produced: development, production, post-production, and release."

### Problem Resolution Analogies

1. **Merge conflicts:**
   - "A merge conflict is like two chefs modifying the same recipe in different ways."
   - "It's like two people editing the same paragraph in a document differently."

2. **Detached HEAD:**
   - "A detached HEAD is like browsing a book without a bookmark - if you move somewhere else, you might lose your place."
   - "It's like visiting a historical site - you can look around but not build there permanently."

3. **Reset vs. Revert:**
   - "Reset is like erasing part of history, while revert is like adding an apology note to history."
   - "Reset is deleting mistakes from your draft; revert is publishing a correction."
