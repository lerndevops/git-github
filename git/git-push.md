# `git push` 🚀

The `git push` command is used to **upload local repository content** to a **remote repository** like GitHub, GitLab, or Bitbucket.

## 🧠 What Does `git push` Do?

`git push` takes your commits from your **local repository** and sends them to the **remote repository**.

![Git Push Flow](https://wac-cdn.atlassian.com/dam/jcr:94dc4a9d-c6f0-4e41-9ab2-ec0d9f6bca0e/git-push-diagram.svg?cdnVersion=164)


## 🧾 Basic Syntax

```bash
git push <remote> <branch>
```

- `<remote>` – Usually `origin` (the default remote name).
- `<branch>` – The branch you want to push (e.g., `main`, `feature-x`).

### Example:
```bash
git push origin main
```

Pushes the `main` branch to the remote `origin`.

---

## 💼 Common Use Cases

### ✅ Push current branch to the default remote

```bash
git push
```

If tracking info is already set, this is all you need.

---

### 🌱 Push a new branch and set upstream

```bash
git push -u origin new-feature
```

- `-u` sets upstream tracking, so future `git push`/`git pull` commands don’t require specifying the branch.

![Upstream Branch](https://i.stack.imgur.com/m9Nk3.png)

---

### 🔁 Push all branches

```bash
git push --all
```

Sends all local branches to the remote.

---

## ⚠️ Notes and Tips

- Always `git pull` before pushing to avoid conflicts.
- Use `git status` to check your current branch and changes.
- Collaborating with others? Pull their updates first.

---

## ❌ Common Errors & Fixes

### 1. Rejected Push – Non-fast-forward

You might see:
```bash
! [rejected]        main -> main (non-fast-forward)
```

Fix it by syncing your local branch:

```bash
git pull --rebase
git push
```

---

### 2. Authentication Errors

![Authentication Error Example](https://docs.github.com/assets/images/help/desktop/sudo-mode-popup.png)

**Fix:**
- Use SSH or [Personal Access Tokens (PAT)](https://github.com/settings/tokens) if passwords are disabled.

---

## 🧭 Summary

| Command | Description |
|--------|-------------|
| `git push` | Pushes current branch to tracked remote branch |
| `git push origin main` | Pushes `main` to `origin` |
| `git push -u origin branch` | Pushes and sets upstream |
| `git push --all` | Pushes all local branches |

---

## 📌 Visual Recap

### Local → Remote Flow

![Local to Remote](https://miro.medium.com/v2/resize:fit:720/format:webp/1*2eQXUgcd1zjGJH6n6pH2IA.png)