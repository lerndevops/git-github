# git getch

`git fetch` is a Git command that downloads updates from a remote repository **without merging them** into your current branch. It keeps your local copy of the remote branches up to date.

---

## 📥 What Does `git fetch` Do?

- Fetches updates from a remote (like `origin`)
- Updates your remote-tracking branches (like `origin/main`)
- Does **not** change your working directory or local branches

---

## 🧠 Syntax

```bash
git fetch <remote-name> <branch-name>
```

Or just:

```bash
git fetch
```

This fetches all branches from the default remote (usually `origin`).

---

## ✅ Example Usage

### 1. Fetch All Remote Updates

```bash
git fetch
```

Downloads all branches and updates `origin/*` references.

---

### 2. Fetch a Specific Branch

```bash
git fetch origin feature-branch
```

Fetches only the `feature-branch` from `origin`.

---

### 3. View Changes After Fetch

After fetching, you can compare branches:

```bash
git diff main origin/main
```

Or switch to the remote-tracking branch:

```bash
git checkout origin/main
```

---

### 4. Combine with Merge or Rebase

To integrate fetched changes:

```bash
git merge origin/main
```
Or:
```bash
git rebase origin/main
```

---

## 🔄 When to Use `git fetch`

- To see what others have pushed before you merge
- To update remote-tracking branches before reviewing changes
- To avoid unexpected conflicts when pulling

---

## 🧾 `git fetch` vs `git pull`

| Feature              | `git fetch`             | `git pull`                  |
|----------------------|--------------------------|------------------------------|
| Merges changes       | No                       | Yes                          |
| Affects working dir  | No                       | Yes                          |
| Safer for review     | ✅ Yes                   | ❌ Not always                |

---

`git fetch` is like checking the mail 📨 — you're downloading updates but not reading them yet. Use it when you want full control over what gets merged into your local code.

