# git `grep` command: Searching Through Code

The `git grep` command allows you to search for strings or patterns in files tracked by Git. It's much faster than standard `grep` because it uses Git's index and supports powerful pattern matching within the repository.

---

## 🔍 Basic Syntax
```bash
git grep [options] <pattern>
```

---

## 📂 Example Repository Structure
```
project/
├── src/
│   └── app.js
├── README.md
└── config.yaml
```

---

## 💡 Common Examples

### 1. Find a Simple String
```bash
git grep 'TODO'
```
Searches for the word "TODO" in tracked files.

### 2. Case-Insensitive Search
```bash
git grep -i 'fixme'
```
Matches "FIXME", "fixme", or any case variation.

### 3. Regex Search
```bash
git grep -e 'function [a-zA-Z_]+'
```
Finds lines where a function is defined.

### 4. Search in a Specific Directory
```bash
git grep 'init' -- src/
```
Limits search to files in the `src/` folder.

### 5. Show Line Numbers
```bash
git grep -n 'console.log'
```
Adds line numbers to matches.

### 6. Search in a Specific Commit or Branch
```bash
git grep 'config' HEAD~2
```
Searches in the version of files from two commits ago.

```bash
git grep 'version' feature/login
```
Searches in the `feature/login` branch.

### 7. Show Only Matching Filenames
```bash
git grep -l 'export'
```
Lists files containing the pattern, not the actual matches.

### 8. Invert Match (Exclude Pattern)
```bash
git grep -v 'debug'
```
Show lines that **do not** contain the word "debug".

---

## ⚙️ Bonus Tips
- Combine with `xargs` to perform actions on matching files
  ```bash
  git grep -l 'error' | xargs grep -i 'critical'
  ```
- Works with `--cached` to search staged files only
  ```bash
  git grep 'API' --cached
  ```

---

## ✅ Summary
| Option | Description |
|--------|-------------|
| `-i` | Case-insensitive search |
| `-n` | Show line numbers |
| `-l` | Show only file names |
| `-v` | Invert match (exclude pattern) |
| `-e` | Use a regular expression |
| `--cached` | Search staged files |

`git grep` is a fast, Git-native way to search your repo. It's ideal for code reviews, debugging, and refactoring tasks.

Use it when you want more precision and performance than traditional `grep` in Git projects.
