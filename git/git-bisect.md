# git `bisect` command: Find the Commit that Introduced a Bug

The `git bisect` command helps you **quickly find the commit that introduced a bug** using binary search. It automatically checks out commits between a known good and bad state, helping you isolate the issue.

Instead of checking every commit manually, using bisect Git narrows it down by automatically checking out a commit halfway between a known good state and a bad state.

---

## 🧰 Basic Workflow
1. Start `git bisect`
2. Mark a bad commit (where the bug exists)
3. Mark a good commit (where everything worked)
4. Test the code as Git checks out intermediate commits
5. Mark each step as good/bad until Git finds the culprit

---

## 🔧 Basic Commands
```bash
git bisect start
```
Start a bisect session.

```bash
git bisect bad
```
Mark the current commit as bad.

```bash
git bisect good <commit>
```
Mark a known good commit.

```bash
git bisect good
```
Mark current commit as good during the process.

```bash
git bisect reset
```
Reset to original branch and end bisect session.

---

## 💡 Example Workflow
### Step 1: Start Bisect
```bash
git bisect start
```

### Step 2: Mark the Bad Commit (usually the current one)
```bash
git bisect bad
```

### Step 3: Mark the Last Known Good Commit
```bash
git bisect good abc123
```
Git will now checkout a commit between `abc123` and `HEAD`.

### Step 4: Test and Mark Each Step
After testing the code:
```bash
git bisect good   # If it works
# or
git bisect bad    # If it doesn't
```
Repeat until Git identifies the first bad commit.

### Step 5: Exit Bisect Mode
```bash
git bisect reset
```
Returns you to your original HEAD.

---

## ⚙️ Automating with Scripts
If you have a script that can check for the bug:
```bash
git bisect run ./test_script.sh
```
Git will run the script at each step to determine good/bad.

---

## ✅ Summary
- `git bisect` is a **powerful debugging tool** that uses binary search.
- Helps quickly pinpoint the commit that introduced a regression.
- Works manually or with automated scripts.
- Always reset with `git bisect reset` when done.

Use it when you're not sure **which commit broke your code**!