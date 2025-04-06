# git `switch` command: Changing Branches Made Easy

Introduced in **Git 2.23**, `git switch` is a user-friendly way to **change branches** or **create and switch to new ones**. 

It's a modern alternative to `git checkout` for switching branches, making Git easier to understand.

---

## 🔁 Basic Syntax
```bash
git switch [options] <branch>
```

---

## 🌿 Switching to an Existing Branch
```bash
git switch main
```
Switches to the `main` branch.

---

## 🌱 Create and Switch to a New Branch
```bash
git switch -c feature/signup-form
```
Creates a new branch called `feature/signup-form` and switches to it.

---

## 🚫 Abort a Switch with Uncommitted Changes
If you have unsaved changes that would be lost:
```bash
git switch new-feature
```
Git will prevent the switch and prompt you to commit or stash your changes.

---

## 💡 Useful Options
| Option | Description |
|--------|-------------|
| `-c` or `--create` | Create a new branch and switch to it |
| `-C` | Create or reset a branch and switch to it |
| `--detach` | Switch to a commit without being on a branch |
| `--discard-changes` | Discard local changes during switch (use with caution) |

---

## 🧪 Switch to a Specific Commit (Detached HEAD)
```bash
git switch --detach <commit-hash>
```
Useful for testing a previous state of the code without affecting branches.

---

## 🆚 `git switch` vs `git checkout`
| Task | `git switch` | `git checkout` |
|------|--------------|----------------|
| Switch branches | ✅ | ✅ |
| Restore files | ❌ | ✅ |
| Safer & simpler | ✅ | ❌ |

Use `git switch` for **branch operations** and `git restore` for **file operations**.

---

## ✅ Summary
- `git switch` makes branch switching more intuitive
- Use `-c` to create and switch in one step
- Avoids confusion compared to older `git checkout`

---

## 📌 Quick Examples
```bash
# Create and switch to a branch
$ git switch -c bugfix/issue-42

# Switch to existing branch
$ git switch main

# Switch to a specific commit (detached)
$ git switch --detach 1a2b3c4d
```

`git switch` is clean, simple, and focused — your new go-to for branch changes!
