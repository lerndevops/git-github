# Understanding `git shortlog` 🧾

The `git shortlog` command provides a **summary of commits per author** in a Git repository. It's often used to get a quick overview of contributor activity.


## 📘 What It Does

It groups commit messages by author and shows how many commits each person made — great for seeing contributions at a glance.

## 📌 Basic Syntax

```bash
git shortlog
```

This command should be run inside a Git repository.

---

## 🔍 Example Output

```bash
$ git shortlog
Alice Johnson (5):
  Add login page
  Fix button layout
  Improve login validation
  Update README
  Add unit tests

Bob Lee (2):
  Initial commit
  Add license
```

---

## 🧪 Common Options

| Command | Description |
|--------|-------------|
| `-s` | Show only the number of commits per author (summary) |
| `-n` | Sort authors by number of commits (descending) |
| `-e` | Show email addresses |
| `-w` | Wrap long commit messages |

---

### 🔹 Example: Just a Summary

```bash
git shortlog -s
```

Output:

```
   5  Alice Johnson
   2  Bob Lee
```

---

### 🔹 Example: Sorted by Number of Commits

```bash
git shortlog -sn
```

Output:

```
   10 Charlie
    7 Alice
    3 Bob
```

---

### 🔹 Example: Include Email Addresses

```bash
git shortlog -se
```

Output:

```
   5  Alice Johnson <alice@example.com>
   2  Bob Lee <bob@example.com>
```

---

### 🔹 Example: View for a Specific Branch

```bash
git shortlog main
```

You can use this to check a particular branch (like `main`, `dev`, etc.).



## 🔍 Use with Git Ranges (Log History)

You can use `git shortlog` in combination with `git log` options:

```bash
git shortlog HEAD~10..HEAD
```

This shows commits per author for the last 10 commits.

## ✅ Use Cases

- Get a **quick breakdown** of contributors.
- Generate simple **project contribution stats**.
- Useful for **open-source maintainers** during release notes.
- Great for **team retrospectives** and **credits**.



## 🧠 Pro Tip

Use `git shortlog` with `--since` or `--until` to filter by time:

```bash
git shortlog -sn --since="1 month ago"
```

## 🧭 Summary

| Option | Meaning |
|--------|---------|
| `-s` | Summary (just counts) |
| `-n` | Sort by number of commits |
| `-e` | Include emails |
| `--since`, `--until` | Filter by date |
| `branch-name` | Limit to a specific branch |

