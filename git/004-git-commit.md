# `git commit`

> git commit is a command in Git used to save changes to the local repository. It captures a snapshot of the project’s current state, allowing you to track changes over time.

### How It Works

> When you modify files in a Git repository, those changes remain untracked until you explicitly add them to the staging area using git add. Once staged, you can use git commit to record the changes permanently in the repository.

### Key Points:

	•	Commits are local: They are saved only in your local repository until you push them to a remote repository (e.g., GitHub, GitLab).
	•	Each commit has a unique ID (SHA-1 hash): This allows you to track specific changes.
	•	Requires a message: A descriptive message (-m "message") is needed to explain what the commit does.

# Demo

## Prerequisites
Make sure you have Git installed. You can check by running:

```sh
git --version
```

If Git is not installed, download and install it from [git-scm.com](https://git-scm.com/).

## 1. Initialize a Git Repository
Navigate to your project folder and initialize Git:

```sh
cd /path/to/your/project
git init
```

## 2. Configure Git (Optional but Recommended)
Set your user name and email:

```sh
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

## 3. Create or Modify Files
Create a new file or modify an existing one:

```sh
echo "Hello, Git!" > example.txt
```

## 4. Check the Status of Your Repository
Use the following command to check changes:

```sh
git status
```

## 5. Stage Files for Commit
Add files to the staging area:

```sh
git add example.txt
```

To add all modified files:

```sh
git add .
```

## 6. Commit Changes
Commit the staged files with a message:

```sh
git commit -m "Initial commit with example.txt"
```

## 7. View Commit History
Check the commit history:

```sh
git log
```

For a concise view:

```sh
git log --oneline --graph
```

## 8. Modify and Commit Again
Make changes and commit again:

```sh
echo "Updated content" >> example.txt
git add example.txt
git commit -m "Updated example.txt"
```

## Conclusion

> git commit is an essential command for version control, allowing you to keep a history of your changes and collaborate effectively.
