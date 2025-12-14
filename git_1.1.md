# Git Commands & Use Cases - Core Reference

## Git vs GitHub
- **Git**: Local version control system that tracks file changes
- **GitHub**: Cloud-based hosting platform for Git repositories

---

## Getting Started

### Installation & Configuration
```bash
git --version                                    # Check Git installation
git config --global user.name "Your Name"        # Set username
git config --global user.email "you@email.com"   # Set email
```

### Repository Initialization
```bash
git init                                         # Initialize local repository
git clone <repo-url>                            # Clone remote repository
```

---

## Tracking Changes

### Check Status & History
```bash
git status                                       # View current changes
git log                                         # View full commit history
git log --oneline                               # View compact commit history
```

### Staging Changes
```bash
git add <file>                                  # Stage specific file
git add .                                       # Stage current directory
git add --all / git add -A                      # Stage all changes (adds, modifications, deletions)
git add *.txt                                   # Stage by file extension
```

### Committing Changes
```bash
git commit -m "message"                         # Commit staged changes
git reset                                       # Unstage all changes
git reset --hard                                # Reset to last commit (discard all changes)
git reset HEAD~                                 # Undo last commit (keep changes)
```

---

## File Operations

### Delete & Restore
```bash
git rm <file>                                   # Delete file and stage deletion
git rm -f <file>                                # Force delete modified file
git rm --cached <file>                          # Untrack file but keep locally
git rm -r <folder>                              # Recursively remove folder
git restore <file>                              # Restore file to last commit
git restore .                                   # Restore all files
git restore --staged <file>                     # Unstage file
```

---

## Branching & Merging

### Branch Management
```bash
git branch                                      # List all branches
git branch <branch-name>                        # Create new branch
git checkout <branch-name>                      # Switch to branch
git checkout -b <branch-name>                   # Create and switch to new branch
```

### Merging
```bash
git merge <branch-name>                         # Merge branch into current branch
git merge <branch> -m "message"                 # Merge with commit message
```

### Merge Conflicts
- Git marks conflicts with `<<<<<<<`, `=======`, `>>>>>>>`
- Manually edit conflicted files
- Stage and commit resolved files

---

## Remote Operations

### Push & Pull
```bash
git push origin <branch>                        # Push local branch to remote
git fetch                                       # Download remote changes (no merge)
git pull                                        # Fetch and merge remote changes
git pull = git fetch + git merge
```

---

## Comparing & Navigating

### View Differences
```bash
git diff <commit-id1> <commit-id2>              # Compare two commits
git checkout <commit-id>                        # Jump to specific commit
git checkout main                               # Return to main branch
```

---

## Advanced Operations

### Stashing (Temporary Storage)
```bash
git stash                                       # Save uncommitted changes
git stash pop                                   # Restore and remove from stash
git stash apply                                 # Restore but keep in stash
git stash list                                  # View all stashes
git stash drop                                  # Remove specific stash
```

### Reverting Changes
```bash
git revert <commit-id>                          # Undo commit by creating new commit
git rebase <branch>                             # Reapply commits on top of another branch
```

**⚠️ Warning**: `git rebase` rewrites history - avoid on shared/public branches

---

## GitHub Workflow

### Pull Requests (PR)
1. Push feature branch to GitHub
2. Create Pull Request on GitHub
3. Team reviews and discusses changes
4. Merge PR into main branch

---

## Key Architecture

```
Working Directory → Staging Area → Local Repository → Remote Repository
        ↓                ↓                ↓                  ↓
   (git add)      (git commit)      (git push)         (GitHub)
```

---

## Common Workflows

### New Feature Development
```bash
git checkout -b feature-branch                  # Create feature branch
# Make changes...
git add .
git commit -m "Add new feature"
git push origin feature-branch                  # Push to remote
# Create Pull Request on GitHub
```

### Syncing with Main
```bash
git checkout main
git pull origin main                            # Get latest changes
git checkout feature-branch
git merge main                                  # Merge main into feature
# or
git rebase main                                 # Rebase feature on main (cleaner history)
```

### Fixing Mistakes
```bash
git restore <file>                              # Undo local changes
git reset HEAD~                                 # Undo last commit
git revert <commit-id>                          # Safely undo pushed commit
```

---

## Best Practices

✅ Commit frequently with clear messages  
✅ Always pull before pushing  
✅ Use branches for new features  
✅ Review changes with `git status` before committing  
✅ Test before merging to main  
✅ Use Pull Requests for collaboration  
✅ Never rebase shared/public branches  

---

## Quick Command Summary

| Command | Purpose |
|---------|---------|
| `git status` | Check current state |
| `git add .` | Stage all changes |
| `git commit -m "msg"` | Save changes |
| `git push origin <branch>` | Upload to remote |
| `git pull` | Download and merge |
| `git branch` | List branches |
| `git checkout <branch>` | Switch branch |
| `git merge <branch>` | Merge branches |
| `git log --oneline` | View history |
| `git stash` | Temporarily save work |

---

**Created**: December 2025  
**Source**: freeCodeCamp Git & GitHub Handbook  
**Author**: Learn with Sumit / Sumit Saha
