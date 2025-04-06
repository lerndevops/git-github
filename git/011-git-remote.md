# `git remote` 🌐

`git remote` is a Git command used to manage connections to **remote repositories**. These are versions of your project hosted online (e.g., on GitHub, GitLab, Bitbucket).

## 🧠 What is a Remote?

A **remote** in Git is a **reference to a remote repository**. It allows you to:

- **Fetch** and **pull** changes from others
- **Push** your own commits
- Collaborate on the same codebase across the internet

## 🧾 Basic Commands

### 🔍 View all remotes

```bash
git remote
```

Shows a list of remote names, like:

```
origin
```

---

### 🔍 View detailed info (URLs)

```bash
git remote -v
```

Output:

```
origin  https://github.com/username/repo.git (fetch)
origin  https://github.com/username/repo.git (push)
```

This shows which URLs Git uses for fetching and pushing.

---

### ➕ Add a remote

```bash
git remote add <name> <url>
```

Example:

```bash
git remote add origin https://github.com/username/repo.git
```

This connects your local repo to a remote GitHub repository.

---

### ❌ Remove a remote

```bash
git remote remove <name>
```

Example:

```bash
git remote remove origin
```

This disconnects the remote.

---

### ✏️ Rename a remote

```bash
git remote rename <old-name> <new-name>
```

Example:

```bash
git remote rename origin upstream
```

---

### 🔄 Change the remote URL

```bash
git remote set-url <name> <new-url>
```

Example:

```bash
git remote set-url origin git@github.com:username/repo.git
```

---

## 🌐 Common Remote Names

| Name      | Meaning                              |
|-----------|--------------------------------------|
| `origin`  | Default name for your main remote    |
| `upstream`| Used when contributing to a forked repo |


## 🔁 Typical Remote Workflow

1. Clone a repository:
   ```bash
   git clone https://github.com/user/repo.git
   ```
   → Automatically sets `origin` as remote.

2. View remotes:
   ```bash
   git remote -v
   ```

3. Add a new remote:
   ```bash
   git remote add upstream https://github.com/original-owner/repo.git
   ```

4. Pull updates:
   ```bash
   git pull upstream main
   ```

5. Push your changes:
   ```bash
   git push origin main
   ```

---

## 🧭 Summary

| Command | Purpose |
|--------|---------|
| `git remote` | List remotes |
| `git remote -v` | Show remotes with URLs |
| `git remote add` | Add a new remote |
| `git remote remove` | Delete a remote |
| `git remote rename` | Rename a remote |
| `git remote set-url` | Change remote URL |