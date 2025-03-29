# git log

git log is a command used in Git to view the history of commits in a repository. It provides detailed information about each commit, such as:

	•	Commit hash
	•	Author name and email
	•	Date and time of the commit
	•	Commit message

# Common `git log` Options

| Option | Description |
|--------|-------------|
| `git log` | Shows the commit history in reverse chronological order. |
| `git log --oneline` | Displays each commit in a single line (short hash + message). |
| `git log --graph` | Shows a visual representation of branches and merges. |
| `git log --all` | Displays commits from all branches. |
| `git log -n <number>` | Limits the output to the last `<number>` commits. |
| `git log --author="name"` | Filters commits by author. |
| `git log --grep="keyword"` | Shows commits that contain a specific word in the message. |
| `git log -p` | Displays changes introduced in each commit. |
| `git log --stat` | Shows a summary of file changes (insertions/deletions). |
| `git log -- file.txt` | Shows commit history for a specific file. |
| `git log --since="2024-01-01"` | Displays commits made after a certain date. |
| `git log --until="2024-01-01"` | Displays commits made before a certain date. |
| `git log --pretty=format:"%h - %an: %s"` | Customizes the log output format. |
| `git log --reverse` | Shows commits in chronological order (oldest first). |

## Prerequisites
- Install Git
- Initialize a Git repository
- Create and commit some files

```sh
# Initialize a Git repository
mkdir git-log-demo && cd git-log-demo
git init

echo "First commit" > file1.txt
git add file1.txt
git commit -m "Initial commit"

echo "Second commit" > file2.txt
git add file2.txt
git commit -m "Added second file"

echo "Third commit" > file3.txt
git add file3.txt
git commit -m "Added third file"
```

## 1. View Commit History
```sh
git log
```
This shows the commit history in reverse chronological order.

## 2. Show One-line Commit Messages
```sh
git log --oneline
```
Displays a concise view with commit hashes and messages.

## 3. Limit the Number of Commits
```sh
git log -n 2
```
Shows only the last two commits.

## 4. View Commits with Graphical Representation
```sh
git log --graph --oneline --all
```
Displays commits in a graphical manner, useful in branches.

## 5. View Commits of a Specific Author
```sh
git log --author="Your Name"
```
Filters commits made by a specific author.

## 6. View Commits Containing a Specific Word
```sh
git log --grep="Initial"
```
Finds commits with messages that contain "Initial".

## 7. View Changes in Each Commit
```sh
git log -p
```
Shows commit history along with the changes introduced.

## 8. View Commit History of a Specific File
```sh
git log -- file1.txt
```
Shows the commit history for `file1.txt`.

## 9. View Commits in a Custom Format
```sh
git log --pretty=format:"%h - %an, %ar : %s"
```
Displays logs in a custom format with abbreviated commit hash, author name, relative time, and commit message.

## 10. View Statistics for Commits
```sh
git log --stat
```
Shows the number of insertions and deletions per file in each commit.
