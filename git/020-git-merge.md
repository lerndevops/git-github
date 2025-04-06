# git merge command

* `git merge` is used to **combine the histories** of two branches. It’s a key part of collaborative workflows in Git.

* git merge is a Git command used to combine changes from one branch into another. It helps bring together the work of multiple contributors or the results of separate development efforts.

---

## 📌 What Does `git merge` Do?

When you merge one branch into another, Git takes the contents of the source branch and integrates them into the target branch. 

By default, this creates a new **merge commit** if the histories of the two branches have diverged.

---

## 🧠 Syntax

```bash
git merge <branch-name>
```

This merges the specified branch into the current branch.

---

## ✅ Basic Example

```bash
git checkout main
git merge feature-branch
```
This merges the changes from `feature-branch` into `main`.

---

## 🔀 Fast-Forward Merge

If the target branch has not diverged, Git performs a fast-forward:

```bash
git checkout main
git merge feature-branch  # Fast-forward if possible
```

No new merge commit is created; Git just moves the pointer.

---

## 🔀 3-Way Merge

If both branches have new commits, Git will create a **merge commit**:

```bash
git merge other-branch
```

---

## ⚔️ Merge Conflicts

If the changes from the branches conflict, Git will pause the merge and ask you to resolve conflicts.

```bash
# After editing conflicting files:
git add <resolved-file>
git commit
```

---

## 🧹 Cancel a Merge

If you're in the middle of a merge and want to abort:

```bash
git merge --abort
```

---

## 🚫 Don't Confuse With

- `git rebase`: re-applies commits on top of another base
- `git pull`: fetches and merges from a remote branch

---

## ✅ Best Practices

- Always pull the latest changes before merging
- Use descriptive commit messages for merge commits
- Resolve conflicts thoughtfully — never blindly accept changes
