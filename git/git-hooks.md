# git hooks

## Introduction

> Git hooks are scripts that run automatically at specific points in the Git workflow, such as before a commit, after a merge, or before pushing changes. They help automate tasks like enforcing coding standards, running tests, or preventing bad commits.

### How Git Hooks Work


>> Git hooks reside in the .git/hooks/ directory of a repository. Each hook is a script (usually a shell script) that Git executes when a specific event occurs. 

>> By default, Git provides sample hook scripts (e.g., pre-commit.sample), which you can rename and modify as needed.

### Types of Git Hooks

> **Git provides two types of hooks:**

	1.	Client-side hooks – Run on local repositories and affect actions like commits, merges, and pushes.
	2.	Server-side hooks – Run on the remote repository and affect actions like receiving pushes.

### Common Git Client-Side Hooks

| Hook Name      | When It Runs | Common Use Case |
|---------------|-------------|-----------------|
| `pre-commit`  | Before committing | Run linters, format code, check for sensitive data |
| `prepare-commit-msg` | Before commit message editor opens | Pre-fill commit messages, add issue numbers |
| `commit-msg`  | Before saving the commit message | Enforce commit message style (e.g., require issue number) |
| `post-commit` | After a commit is made | Notify team, trigger scripts, log commit data |
| `pre-rebase`  | Before a rebase starts | Prevent rebasing certain branches, validate commits |
| `post-rewrite` | After a commit is modified (e.g., rebase, amend) | Update logs, notify teams |
| `pre-push`    | Before pushing changes to remote | Run tests, check dependencies, prevent bad pushes |
| `post-checkout` | After `git checkout` | Set up dependencies or configurations |
| `post-merge`  | After a merge is completed | Run migrations, notify team, update dependencies |
| `post-receive` | After remote receives a push (on a remote repo) | Trigger CI/CD pipelines, deploy code |


### Common Git Server-Side Hooks

| Hook Name      | When It Runs | Common Use Case |
|---------------|-------------|-----------------|
| `pre-receive` | Before accepting a push | Enforce policies (e.g., no force pushes, branch protection) |
| `update`      | Before updating refs | Validate branch updates, restrict changes |
| `post-receive` | After receiving a push | Trigger CI/CD pipelines, notify teams, deploy code |
| `pre-auto-gc` | Before Git runs auto garbage collection | Prevent auto GC under certain conditions |
| `post-update` | After a ref is updated | Inform users, update external services |
| `reference-transaction` | When a reference is created, updated, or deleted | Audit and enforce security policies |



# Demo 

## Step 1: Locate the Hooks Directory
Each Git repository has a `.git/hooks/` directory containing sample hook scripts.

```sh
ls .git/hooks/
```

This will list sample hooks such as `pre-commit.sample` and `pre-push.sample`.

## Step 2: Create a Custom Hook
To create a custom hook, navigate to the `.git/hooks/` directory and create a new script. Here’s an example of a `pre-commit` hook that prevents commits with debug statements.

```sh
touch .git/hooks/pre-commit
chmod +x .git/hooks/pre-commit
```

Now, open `pre-commit` in a text editor and add the following script:

```sh
#!/bin/sh

# Prevent commits containing 'console.log' (JavaScript) or 'print' (Python)
if git diff --cached | grep -E 'console\.log|print\('; then
  echo "❌ Commit rejected: Remove debug statements before committing."
  exit 1
fi

exit 0
```

## Step 3: Test the Hook
1. Add a debug statement in a file:
   ```sh
   echo "console.log('Debugging');" > test.js
   git add test.js
   ```
2. Try committing the file:
   ```sh
   git commit -m "Test commit"
   ```
3. The hook should prevent the commit if debug statements are found.

## Step 4: Using Other Git Hooks
| Hook Name      | Trigger Event | Common Use Case |
|---------------|--------------|-----------------|
| pre-commit   | Before commit | Run linters, format code, check for sensitive data |
| commit-msg   | Before commit message is saved | Enforce commit message style |
| pre-push     | Before `git push` | Run tests, check dependencies |
| post-merge   | After a successful merge | Run migrations, notify team |

## Step 5: Share Hooks Across a Team
By default, hooks are not shared when cloning a repository. To share them:
1. Store hooks in a custom directory (e.g., `.githooks/`).
2. Configure Git to use this directory:
   ```sh
   git config core.hooksPath .githooks/
   ```
3. Add custom hooks to `.githooks/` and commit them.

## More Examples

## Commit Message Hook: Enforce Conventional Commit Format
```sh 
touch .git/hooks/commit-msg
vi .git/hooks/commit-msg
```
```sh 
#!/bin/sh

commit_msg=$(cat "$1")

# Regex for valid commit format (e.g., feat: fix: chore: etc.)
if ! echo "$commit_msg" | grep -E -q "^(feat|fix|chore|docs|style|refactor|test|perf|ci): .+"; then
  echo "❌ Commit message must follow Conventional Commit format (e.g., 'feat: add login button')."
  exit 1
fi

exit 0
```

## Pre-Push Hook: Run Tests Before Pushing
```sh
touch .git/hooks/pre-push
vi .git/hooks/pre-push
```
```sh 
#!/bin/sh

echo "🔍 Running tests before pushing..."
npm test  # Change this command based on your test framework

if [ $? -ne 0 ]; then
  echo "❌ Tests failed! Fix errors before pushing."
  exit 1
fi

echo "✅ All tests passed. Proceeding with push."
exit 0
```

---

## 4. Post-Commit Hook: Notify Team on Slack
This **post-commit** hook sends a Slack notification after every commit.

### **Script (`.git/hooks/post-commit`)**
```sh
#!/bin/sh

COMMIT_MSG=$(git log -1 --pretty=format:"%h - %s")
SLACK_WEBHOOK_URL="https://hooks.slack.com/services/YOUR/SLACK/WEBHOOK"

curl -X POST -H 'Content-type: application/json' --data "{
    \"text\": \"New commit: $COMMIT_MSG\"
}" $SLACK_WEBHOOK_URL
```

---

## 5. Pre-Receive Hook: Block Large Files on Remote
This **pre-receive** hook (server-side) blocks pushes containing files larger than 5MB.

### **Script (`.git/hooks/pre-receive`)**
```sh
#!/bin/sh

MAX_SIZE=5000000  # 5MB

while read oldrev newrev refname; do
  for file in $(git diff --name-only $oldrev $newrev); do
    if [ $(git cat-file -s :$file) -gt $MAX_SIZE ]; then
      echo "❌ Push rejected: File $file is too large (over 5MB)."
      exit 1
    fi
  done
 done

exit 0
```

---

## 6. Post-Receive Hook: Deploy to Server
This **post-receive** hook (server-side) deploys the latest code after a push.

### **Script (`.git/hooks/post-receive`)**
```sh
#!/bin/sh

DEPLOY_DIR="/var/www/myproject"
GIT_REPO="/home/user/repo.git"

echo "🚀 Deploying latest changes..."
cd $DEPLOY_DIR || exit
git --work-tree=$DEPLOY_DIR --git-dir=$GIT_REPO checkout -f main
systemctl restart myapp  # Restart application

echo "✅ Deployment complete!"
exit 0
```

---

## 7. Pre-Rebase Hook: Prevent Rebase on Protected Branches
This **pre-rebase** hook prevents users from rebasing the `main` or `develop` branches.

### **Script (`.git/hooks/pre-rebase`)**
```sh
#!/bin/sh

PROTECTED_BRANCHES=("main" "develop")

current_branch=$(git rev-parse --abbrev-ref HEAD)

for branch in "${PROTECTED_BRANCHES[@]}"; do
  if [ "$current_branch" = "$branch" ]; then
    echo "❌ Rebase is not allowed on the $branch branch."
    exit 1
  fi
done

exit 0
```

