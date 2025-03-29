# Git Stash Step-by-Step Guide

## What is Git Stash?

> git stash is a Git command that temporarily saves (or “stashes”) changes that are not yet committed, allowing you to switch branches or work on something else without losing progress. 

> It helps keep your working directory clean while preserving your changes for later use.

> **OR** Git stash allows you to temporarily save changes that are not yet ready to be committed, so you can work on something else and then come back to them later.

## Step-by-Step Guide

### 1. Check the Current Status
```sh
git status
```
This will show any modified or untracked files in your working directory.

### 2. Stash Your Changes
```sh
git stash
```
This command saves your local modifications and reverts your working directory to the last committed state.

### 3. List Stashed Changes
```sh
git stash list
```
This command shows a list of stashed changes.

Example output:
```
stash@{0}: WIP on main: abc1234 Commit message
stash@{1}: WIP on feature-branch: def5678 Another commit message
```

### 4. Apply Stashed Changes
```sh
git stash apply stash@{0}
```
This will apply the latest stashed changes (or a specific stash if specified).

### 5. Drop a Stash
```sh
git stash drop stash@{0}
```
Use this to remove a specific stash after applying it.

### 6. Apply and Remove Stash in One Command
```sh
git stash pop
```
This applies the latest stash and removes it from the stash list.

### 7. Clear All Stashes
```sh
git stash clear
```
Use this to delete all stashed changes permanently.

### 8. Stash Untracked Files
By default, `git stash` ignores untracked files. To include them, use:
```sh
git stash -u
```

### 9. Stashing with a Message
To add a custom message to a stash, use:
```sh
git stash push -m "WIP: Fixing bug in feature-branch"
```

### 10. Creating a Branch from a Stash
If you want to create a new branch from a stash:
```sh
git stash branch new-branch-name stash@{0}
```
This will create and switch to a new branch with the stashed changes applied.

## Conclusion
Git stash is a powerful tool to manage temporary changes efficiently. It allows you to switch tasks without losing progress on your current work.
