# git `mv` command: Move or Rename Files in Git

The `git mv` command is used to move or rename files and update the Git index accordingly. It’s essentially a shortcut for moving/renaming a file and then staging the change in one step.

---

## 🔧 Basic Syntax
```bash
git mv <source> <destination>
```

This moves or renames a file from `<source>` to `<destination>` and stages the change automatically.

---

## 🎯 Why Use `git mv`?
- Renames or moves a file and stages the change
- Keeps file history intact (if possible)
- Cleaner than using `mv` + `git add` + `git rm`

---

## 💡 Examples

### 1. Rename a File
```bash
git mv old_name.txt new_name.txt
```
This renames the file and stages the change.

### 2. Move a File to a Folder
```bash
git mv file.txt folder/file.txt
```
This moves the file to a new directory and stages it.

### 3. Move and Rename
```bash
git mv notes.txt docs/meeting-notes.md
```
Moves `notes.txt` to `docs/` folder and renames it in one go.

---

## 🛠️ Manual Alternative (Not Recommended)
You can achieve the same result manually:
```bash
mv file.txt new_folder/file.txt
git add new_folder/file.txt
git rm file.txt
```
But using `git mv` is cleaner and less error-prone.

---

## 📌 Notes
- Git tracks content, not files. So even if you use system `mv`, Git will detect renames if the content stays mostly the same.
- `git mv` helps you **stage** the rename/move cleanly.
- If the destination path doesn’t exist, it will be created automatically.

---

## ✅ Summary
`git mv` simplifies the process of renaming or moving files within your Git repository. It handles both the file system operati