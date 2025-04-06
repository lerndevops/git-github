# git `reset` command: Rewriting History Safely

The `git reset` command is used to **undo changes** by moving the current branch pointer and, optionally, modifying the staging area and working directory. It’s a powerful (and sometimes dangerous) tool for rewriting local history.

### 🧠 What Does It Affect?
- **Commit History**
- **Staging Area (Index)**
- **Working Directory**

> **Depending on the mode used: `--soft`, `--mixed`, or `--hard`.**

---

> **This table summarizes the behavior of the three primary modes of the `git reset` command.**

| Mode       | Moves HEAD | Affects Staging Area | Affects Working Directory | Description                                      |
|------------|------------|----------------------|----------------------------|--------------------------------------------------|
| `--soft`   | ✅         | ❌                   | ❌                         | Undo commit(s), keep changes staged             |
| `--mixed`  | ✅         | ✅                   | ❌                         | Undo commit(s), unstage changes                 |
| `--hard`   | ✅         | ✅                   | ✅                         | Undo commit(s), discard all local changes       |


> **⚠️ Use `--hard` with caution, it permanently deletes uncommitted changes from your working directory.**
---

## 🔧 Basic Syntax
```bash
git reset [<mode>] [<commit>]
```

---

## 🎯 Reset Modes

### 1. `--soft`: Move HEAD Only
```bash
git reset --soft HEAD~1
```
- Keeps working directory and staging area.
- Moves `HEAD` back one commit.
- Useful when you want to uncommit but keep your changes staged.

### 2. `--mixed` (default): Unstage Changes
```bash
git reset --mixed HEAD~1
# or simply:
git reset HEAD~1
```
- Moves `HEAD` and resets the **staging area**.
- Keeps working directory unchanged.
- Useful for unstaging files.

### 3. `--hard`: Discard Everything
```bash
git reset --hard HEAD~1
```
- Resets `HEAD`, staging area, **and working directory**.
- **WARNING:** This deletes changes permanently!

---

## 🔙 Reset to a Specific Commit
```bash
git reset --hard abc1234
```
Resets to a specific commit hash.

---

## 🧼 Unstage Specific Files
```bash
git reset HEAD file.txt
```
Unstages `file.txt` while keeping changes in the working directory.

---

## 🆚 `git reset` vs `git revert`
| Command | Changes Commit History? | Safe for Shared Branches? |
|---------|--------------------------|----------------------------|
| `reset` | ✅ Yes                   | ❌ No                      |
| `revert` | ❌ No                   | ✅ Yes                     |

Use `git reset` only on local branches you haven’t pushed.
