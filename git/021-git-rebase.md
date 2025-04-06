# git rebase

* `git rebase` is a Git command that moves the entire branch to begin on a new base commit. It’s mostly used to make your Git history cleaner and more linear.

### Why Use Rebase?

> Let’s say you’ve been working on a feature in a separate branch while the main branch has moved forward. You can use git rebase to replay your feature branch commits on top of the updated main branch — like pretending you started from the latest code.

## 🧠 Syntax

```bash
git rebase <base-branch>
```

---

## ✅ Basic Example

```bash
git checkout feature-branch
git rebase main
```
This re-applies the commits from `feature-branch` on top of the latest `main` branch.

---

## 📉 Before vs. After

Before rebase:
```
main:      A---B---C
                  \
feature:           D---E
```

After rebase:
```
main:      A---B---C---D'---E'
```
(commits D and E are reapplied as D' and E')

## ⚔️ Rebase Conflicts

If there are conflicts, Git will stop and ask you to resolve them:
```bash
# After resolving conflicts:
git add <file>
git rebase --continue
```
To cancel the rebase:
```bash
git rebase --abort
```

---

## 🚫 Caution!

- Never rebase **shared/public branches** (e.g., `main`, `develop`) because it rewrites history.
- Use rebase for **local** cleanup or keeping branches up to date before a pull request.

---

## ✅ Rebase vs Merge

| Feature         | `git merge`         | `git rebase`             |
|-----------------|---------------------|---------------------------|
| History         | Keeps all commits   | Rewrites commit history   |
| Merge commit    | Yes (default)       | No                        |
| Use case        | Preserving history  | Streamlining history      |
