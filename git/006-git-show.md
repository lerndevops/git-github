# `git show`

## Introduction


> `git show` is a Git command used to display detailed information about Git objects, such as commits, tags, and blobs. 

> It provides a combination of metadata (commit hash, author, date, commit message) and changes (diff) in a single command.

### syntax 

```sh
git show [options] [object]
```

	•	[object] can be a commit hash, a tag, or another Git object.
	•	[options] allow customization of the output.

## Prerequisites
- Git installed on your system
- A Git repository (either existing or a new one)

## Step 1: Set Up a Git Repository
If you don’t already have a Git repository, create one by running:

```sh
mkdir git-show-demo
cd git-show-demo
git init
```

## Step 2: Create and Commit a File
Create a sample file and commit it.

```sh
echo "Hello, Git Show!" > demo.txt
git add demo.txt
git commit -m "Initial commit with demo.txt"
```

## Step 3: Use `git show`
Now, use the `git show` command to display the details of the last commit.

```sh
git show
```

This will output details like:
- Commit hash
- Author details
- Date
- Commit message
- Changes made in the commit

## Step 4: Show a Specific Commit
Find the commit hash using:

```sh
git log --oneline
```

Then, use `git show` with the specific commit hash:

```sh
git show <commit-hash>
```

Replace `<commit-hash>` with the actual commit ID.

## Step 5: Show File Changes from a Commit
To see changes for a specific file in a commit:

```sh
git show <commit-hash> -- demo.txt
```

## Step 6: Show Changes in a Different Format
You can also display commit changes in a different format:

- **Show commit in short format:**
  ```sh
  git show --stat
  ```
- **Show patch without commit message:**
  ```sh
  git show --pretty=short
  ```

## When to Use git show?

	•	When you need to inspect a commit in detail.
	•	When reviewing changes made to a specific file in a commit.
	•	When checking commit metadata without navigating through git log.
	•	When examining the details of an annotated tag.

## Conclusion
The `git show` command is a powerful way to inspect commit details and changes in a repository. Experiment with different options to get comfortable using it in your workflow!


# Advanced use cases

## Show Commit with Word-Level Diff
Highlight changes at the word level:

```sh
git show --word-diff
```

## Show Only Specific Parts of a Commit
- **Show only the commit message:**
  ```sh
  git show -s --format=%B <commit-hash>
  ```
- **Show only the author name:**
  ```sh
  git show -s --format=%an <commit-hash>
  ```
- **Show only the date:**
  ```sh
  git show -s --format=%ci <commit-hash>
  ```

## Show Changes in a Specific File Format
To see changes only in Markdown or JSON files:

```sh
git show <commit-hash> -- '*.md'
git show <commit-hash> -- '*.json'
```

## Compare Two Commits
To compare changes introduced in a specific commit:

```sh
git show <commit1>..<commit2>
```

Example:
```sh
git show a1b2c3d..d4e5f6g
```

## Show What a Tag Points To
For annotated tags:

```sh
git show v1.0.0
```

## Show Commit in Custom Pretty Format
Format commit details cleanly:

```sh
git show --pretty=format:"%h - %an, %ar : %s"
```

Example output:
```
a1b2c3d - Alice, 2 hours ago : Fixed issue #42
```

## Show Raw Patch Format
To save a patch for later use:

```sh
git show <commit-hash> > fix_bug.patch
```

Apply the patch later with:

```sh
git apply fix_bug.patch
```

## Show Metadata Only (No Diff)
Display commit metadata without file changes:

```sh
git show --no-patch
```

## Show Differences with Colorized Output
Highlight additions and deletions:

```sh
git show --color
```

## Show Object Type and Raw Contents
Check what type of Git object you’re dealing with:

```sh
git cat-file -t <object-hash>
git cat-file -p <object-hash>
```