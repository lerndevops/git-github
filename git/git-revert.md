# Git Revert Demo

## Introduction
`git revert` is a command used to undo changes in Git by creating a new commit that reverses a previous commit.

## How git revert Works

> Instead of deleting a commit, git revert generates a new commit that applies the inverse of the changes made in a previous commit. This ensures that history remains intact, making it useful when working in shared repositories.

## When to Use git revert

	•	When you need to undo a commit without removing it from history.
	•	When you want to keep a clear record of what was undone.

## Steps to Use `git revert`

### 1. Initialize a Git Repository
```sh
mkdir git-revert-demo
cd git-revert-demo
git init
```

### 2. Create and Commit a File
```sh
echo "Initial commit" > file.txt
git add file.txt
git commit -m "Initial commit"
```

### 3. Make Another Commit
```sh
echo "New change" >> file.txt
git add file.txt
git commit -m "Added new change"
```

### 4. View Commit History
```sh
git log --oneline
```
Example output:
```
abcd123 Added new change
1234abc Initial commit
```

### 5. Revert the Last commit `OR`  Revert the changes of a specific commit
```sh
git revert HEAD 

OR 

git revert <commitid>
```
This creates a new commit that undoes the changes from `HEAD` (the last commit). `OR` the commit choosen

### 6. Check the History Again
```sh
git log --oneline
```
Example output:
```
5678def Revert "Added new change"
abcd123 Added new change
1234abc Initial commit
```

## Conclusion
`git revert` is a safe way to undo changes because it preserves the commit history while negating specific changes.
