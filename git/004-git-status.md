# git status

The `git status` command provides information about the current state of the working directory and staging area. It helps you understand,

✅ Untracked: New files not yet added to 

✅ Modified: Tracked files that have been changed but not staged

✅ Staged: Changes that are ready to be committed

✅ Committed: No changes to commit, everything is up to date

---

## **1. Checking the Status of a Repository**
To see the current status of your repository, run:

```sh
git status
```

### **Example Output (Clean Repository)**
```
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

This means there are no changes in the working directory or staging area.

---

## **2. Checking Untracked Files**
If you create a new file without staging it, Git will recognize it as untracked.

```sh
touch newfile.txt
git status
```

### **Example Output**
```
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	newfile.txt

nothing added to commit but untracked files present (use "git add" to track)
```

---

## **3. Checking Modified Files**
If you modify a tracked file, Git will detect the change.

```sh
echo "Hello World" > existingfile.txt
git status
```

### **Example Output**
```
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   existingfile.txt
```

---

## **4. Checking Staged Changes**
After staging a file with `git add`, Git moves it to the staging area.

```sh
git add existingfile.txt
git status
```

### **Example Output**
```
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	modified:   existingfile.txt
```

---

## **5. Checking Changes After Commit**
Once you commit changes, Git will show a clean working directory.

```sh
git commit -m "Updated existing file"
git status
```

### **Example Output**
```
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

---

## **6. Checking Ahead or Behind Remote Branch**
If your local branch has diverged from the remote branch, `git status` will notify you.

### **Example Output (Local Ahead of Remote)**
```
On branch main
Your branch is ahead of 'origin/main' by 2 commits.
  (use "git push" to publish your local commits)
```

To sync changes, run:
```sh
git push origin main
```

## **Conclusion**
The `git status` command is essential for tracking changes in your working directory and staging area. Use it frequently to stay informed about your repository’s state and avoid committing unintended changes. 🚀
