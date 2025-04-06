# git `branch` command: Managing Branches

The `git branch` command allows you to **list, create, delete, and manage branches** in a Git repository. Branches are used to isolate work and make collaboration easier.

A branch is like a separate workspace where you can make changes to your code without affecting the main codebase (usually main or master).

---

## 📘 Basic Syntax
```bash
git branch [options] [branch-name]
```

---

## 📄 View Branches
### List All Local Branches
```bash
git branch
```
Shows a list of local branches. The current branch is marked with `*`.

### List All Local and Remote Branches
```bash
git branch -a
```
Displays both local and remote branches.

---

## 🌱 Creating Branches
### Create a New Branch
```bash
git branch feature/login
```
Creates a branch called `feature/login` without switching to it.

### Create and Switch in One Step (Recommended)
```bash
git checkout -b feature/login
# or
git switch -c feature/login
```
Creates and switches to `feature/login`.

---

## 🔁 Switching Branches
```bash
git checkout develop
# or
git switch develop
```
Switches to the `develop` branch.

---

## ❌ Deleting Branches
### Delete a Local Branch (Safe)
```bash
git branch -d feature/login
```
Deletes the branch if it has been merged.

### Force Delete a Local Branch
```bash
git branch -D feature/login
```
Deletes the branch regardless of its merge status.

### Delete a Remote Branch
```bash
git push origin --delete feature/login
```
Deletes the branch from the remote repository.

---

## 🔄 Rename a Branch
### Rename Current Branch
```bash
git branch -m new-name
```
Renames the current branch.

### Rename Another Branch
```bash
git branch -m old-name new-name
```
Renames `old-name` to `new-name`.

---

## ✅ Summary
| Command | Description |
|---------|-------------|
| `git branch` | List local branches |
| `git branch -a` | List all (local + remote) branches |
| `git branch <name>` | Create a new branch |
| `git branch -d <name>` | Delete a merged branch |
| `git branch -D <name>` | Force delete a branch |
| `git branch -m <new>` | Rename current branch |
| `git branch -m <old> <new>` | Rename a specific branch |

---

## 💡 Best Practices
- Use descriptive names like `feature/signup-page` or `bugfix/login-error`
- Regularly delete stale branches
- Prefer `git switch` for better readability
- Use `git branch --merged` to identify branches safe to delete

Git branches keep your development organized and your history clean—learn them well and they'll save you time!
