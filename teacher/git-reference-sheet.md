# Git Command Reference Sheet

## Setup & Configuration

```bash
# Set identity
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Set default editor
git config --global core.editor "code --wait"  # For VS Code

# Set default branch name
git config --global init.defaultBranch main

# List configuration
git config --list

# Set colorful output
git config --global color.ui auto

# Set credential helper
git config --global credential.helper cache  # Cache for 15 minutes
git config --global credential.helper 'cache --timeout=3600'  # Cache for 1 hour
```

## Repository Initialization

```bash
# Initialize a new repository
git init

# Clone an existing repository
git clone https://github.com/username/repository.git

# Clone to a specific directory
git clone https://github.com/username/repository.git my-project

# Clone a specific branch
git clone -b branch-name https://github.com/username/repository.git
```

## Basic Snapshotting

```bash
# Check status
git status
git status -s  # Short format

# Track new files
git add file.txt
git add .  # All files in current directory

# Stage modified files
git add -u  # Only modified tracked files

# Interactive staging
git add -p  # Choose hunks of changes to stage

# Commit staged changes
git commit -m "Commit message"

# Stage tracked files and commit
git commit -am "Commit message"

# Amend previous commit
git commit --amend
git commit --amend --no-edit  # Don't change message
```

## History & Difference

```bash
# Show commit history
git log
git log --oneline  # One line per commit
git log --graph  # ASCII graph of branches
git log --stat  # With changed files statistics
git log -p  # With patches (diffs)
git log --author="name"  # Filter by author
git log --since="2 weeks ago"  # Filter by date
git log --grep="pattern"  # Filter by commit message

# Show changes between commits
git diff  # Working directory vs staging area
git diff --staged  # Staging area vs last commit
git diff HEAD  # Working directory vs last commit
git diff HEAD~1 HEAD  # Previous commit vs last commit
git diff branch1..branch2  # Between branches
git diff commit1..commit2  # Between commits

# Show a specific commit
git show commit-hash
git show HEAD  # Most recent commit
git show HEAD~3  # Three commits back

# Blame (who changed what)
git blame file.txt
git blame -L 10,20 file.txt  # Lines 10-20 only
```

## Branching & Merging

```bash
# List branches
git branch  # Local branches
git branch -r  # Remote branches
git branch -a  # All branches

# Create a branch
git branch branch-name

# Switch branches
git checkout branch-name
git switch branch-name  # Git 2.23+

# Create and switch in one command
git checkout -b branch-name
git switch -c branch-name  # Git 2.23+

# Rename a branch
git branch -m old-name new-name

# Delete a branch
git branch -d branch-name  # Safe delete
git branch -D branch-name  # Force delete

# Merge a branch
git merge branch-name
git merge --no-ff branch-name  # Create merge commit always

# Abort a merge
git merge --abort

# Merge specific files from another branch
git checkout branch-name -- path/to/file
```

## Remote Repositories

```bash
# List remotes
git remote
git remote -v  # With URLs

# Add remote
git remote add origin https://github.com/username/repository.git

# Change remote URL
git remote set-url origin https://github.com/username/new-repository.git

# Fetch changes
git fetch origin
git fetch --all  # All remotes

# Pull changes (fetch + merge)
git pull
git pull origin branch-name
git pull --rebase  # Rebase instead of merge

# Push changes
git push origin branch-name
git push -u origin branch-name  # Set upstream
git push --force  # Force push (USE WITH CAUTION)
git push --force-with-lease  # Safer force push
```

## Stashing

```bash
# Stash changes
git stash
git stash save "Work in progress"

# List stashes
git stash list

# Show stash contents
git stash show
git stash show -p  # With patch

# Apply stash (keep in stash list)
git stash apply
git stash apply stash@{2}  # Specific stash

# Apply and remove stash
git stash pop
git stash pop stash@{2}  # Specific stash

# Remove stash
git stash drop stash@{1}
git stash clear  # Remove all stashes
```

## Advanced Operations

```bash
# Rebase
git rebase main  # Rebase current branch onto main
git rebase -i HEAD~3  # Interactive, last 3 commits
git rebase --abort  # Abort rebase
git rebase --continue  # Continue after resolving conflicts

# Cherry-pick
git cherry-pick commit-hash
git cherry-pick commit1..commit2  # Range of commits

# Reset
git reset --soft HEAD~1  # Undo commit, keep changes staged
git reset HEAD~1  # Undo commit, keep changes unstaged
git reset --hard HEAD~1  # Undo commit, discard changes

# Revert
git revert commit-hash  # Create new commit that undoes changes

# Reflog (reference logs)
git reflog  # History of HEAD changes
git reflog show branch-name  # Branch reference history

# Clean
git clean -n  # Dry run, show what would be deleted
git clean -f  # Delete untracked files
git clean -fd  # Delete untracked files and directories
```

## Tags

```bash
# List tags
git tag
git tag -l "v1.*"  # Pattern matching

# Create tags
git tag v1.0.0  # Lightweight tag
git tag -a v1.0.0 -m "Version 1.0.0"  # Annotated tag

# Create tag for previous commit
git tag -a v1.0.0 commit-hash -m "Version 1.0.0"

# Delete tag
git tag -d v1.0.0

# Push tags
git push origin v1.0.0  # Specific tag
git push --tags  # All tags
```

## Debugging

```bash
# Find which commit introduced a bug
git bisect start
git bisect bad  # Current version is bad
git bisect good v1.0.0  # This version was good
# Git checks out commits, test each one
git bisect good  # Current checkout is good
git bisect bad  # Current checkout is bad
git bisect reset  # End bisect session

# Find commits with specific content
git log -S"function name"  # Find when function was added
git log -G"regex pattern"  # With regex

# Show all commits that changed a file
git log --follow -- path/to/file
```

## Submodules

```bash
# Add submodule
git submodule add https://github.com/username/repository.git path/to/submodule

# Initialize submodules after clone
git submodule init
git submodule update

# Clone with submodules
git clone --recurse-submodules https://github.com/username/repository.git

# Update all submodules
git submodule update --remote
```

## Worktrees

```bash
# Create a new worktree
git worktree add ../path/to/folder branch-name

# List worktrees
git worktree list

# Remove a worktree
git worktree remove ../path/to/folder
```

## Git Hooks

```bash
# Common hook locations (in .git/hooks/)
pre-commit
prepare-commit-msg
commit-msg
post-commit
pre-push

# Enable a hook
chmod +x .git/hooks/pre-commit
```

## Configuration Tips

```bash
# Helpful aliases
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.visual '!gitk'
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"

# Auto-correct typos
git config --global help.autocorrect 1

# Set pull behavior
git config --global pull.rebase true  # Use rebase instead of merge
git config --global pull.ff only  # Fast-forward only
```

## Troubleshooting

```bash
# Check file history
git log -- filename
git log --full-history -- filename  # Include renames

# Find lost commits
git fsck --full

# Fix detached HEAD
git checkout -b new-branch-name  # Create branch at current detached HEAD

# Recover deleted branch (if recent)
git checkout -b recover-branch commit-hash  # If you know the hash
git reflog  # Find the hash if unknown

# Fix "refusing to merge unrelated histories"
git pull origin branch-name --allow-unrelated-histories

# Unstage all files
git reset

# Find large files in history
git rev-list --objects --all | grep -f <(git verify-pack -v .git/objects/pack/*.idx | sort -k 3 -n | tail -10 | awk '{print $1}')
```
