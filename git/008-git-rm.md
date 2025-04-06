# git `rm` Command: Remove Files from a Git Repository

The `git rm` command is used to **remove files from your working directory and stage the deletion** for the next commit. It's useful when you want to stop tracking a file or delete it completely from both your local project and version history.

---

## 🧰 Basic Syntax
```bash
git rm <file>
```

This removes the file from your working directory and stages it for deletion.

---

## 🎯 Why Use `git rm`?
- Cleanly deletes files from both disk and Git index
- Stages the deletion for your next commit
- Supports recursive and forced deletion options

---

## 💡 Examples

### 1. Remove a Single File
```bash
git rm old_script.py
```
This deletes `old_script.py` and stages the change.

### 2. Remove Multiple Files
```bash
git rm temp1.txt temp2.txt
```
Removes multiple files in one command.

### 3. Remove a File But Keep It Locally
```bash
git rm --cached config.json
```
This **unstages** the file and tells Git to stop tracking it, but **keeps it on disk**.

Useful for removing sensitive or auto-generated files.

### 4. Remove Files Recursively
```bash
git rm -r old_directory/
```
Removes a directory and all files inside it.

---

## ⚠️ Caution
Once you commit the `git rm` change, the file is gone from your project history unless you retrieve it from a previous commit.

---

## 📌 Notes
- Always double-check before running `git rm`, especially with `-r` or `--force`.
- Use `.gitignore` to prevent files from being re-added accidentally.

---

## ✅ Summary
`git rm` is a powerful command to clean up your Git repository. Use it to delete or untrack files in a safe, version-controlled way.

It keeps your commit history tidy and helps maintain a clean working environment.