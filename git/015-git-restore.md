# git `restore` command:   Revert Changes in Your Working Directory

The `git restore` command is used to restore files in the working directory to a specific state. It's part of newer Git versions (2.23+) and provides a clearer alternative to older commands like `git checkout` for file restoration.

---

## 🧰 Basic Syntax
```bash
git restore [options] <file>
```

---

## 🎯 What Can `git restore` Do?
- Discard uncommitted changes to a file
- Restore a file to the last committed version
- Unstage files from the staging area

---

## 💡 Examples

### 1. Discard Local Changes in a File
```

git restore main.py
```
Reverts `main.py` to the last committed state (HEAD). Local changes are lost!

### 2. Discard Changes in Multiple Files
```bash
git restore file1.txt file2.txt
```
Useful when you want to wipe changes in multiple files.

### 3. Unstage a File (Move from Staged to Unstaged)
```bash
git restore --staged app.js
```
Removes `app.js` from the staging area, but keeps your changes in the working directory.

### 4. Restore a File from a Specific Commit
```bash
git restore --source=abc123 file.txt
```
Replaces `file.txt` with its version from commit `abc123`.

---

## 🛠️ Comparison: `restore` vs `checkout`
| Action | `git restore` | `git checkout` |
|--------|----------------|-----------------|
| Restore file | ✅ | ✅ |
| Switch branches | ❌ | ✅ |
| Unstage file | ✅ (with `--staged`) | ✅ (older method) |

Use `git restore` for files and `git switch` for branches (modern Git practice).

---

## ⚠️ Caution
- Restoring a file **removes all uncommitted changes**.
- Always double-check before using without `--staged`, especially on important files.

---

## ✅ Summary
`git restore` is a clean, focused command for undoing changes in your working directory or staging area. It simplifies the Git experience and helps avoid common mistakes made with `checkout`.

Use it to confidently manage your file states in a modern Git workflow