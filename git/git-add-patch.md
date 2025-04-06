# git `add -p`: Patch Staging

The `git add -p` (short for `--patch`) command allows you to interactively stage **parts** of files (called *hunks*) rather than whole files. This is ideal for breaking up changes into clean, focused commits.

---

## 🚀 Why Use `git add -p`?
- Stage only the relevant changes for a commit
- Split unrelated changes into separate commits
- Improve code review clarity
- Prevent accidentally committing debugging code or incomplete work

---

## 🧰 Basic Usage
```bash
git add -p
```
This will walk you through each change (hunk) one at a time and prompt you for what to do.

---

## 📋 Example Output
```bash
*** Begin Patch ***
diff --git a/app.js b/app.js
index 1234567..89abcde 100644
--- a/app.js
+++ b/app.js
@@ -10,6 +10,7 @@ function greet() {
   console.log("Hello World");
+  console.log("This is a patch test");
 }
*** End Patch ***
Stage this hunk [y,n,q,a,d,s,e,?]?
```

---

## 🧭 Patch Mode Options
| Key | Action |
|-----|--------|
| `y` | Stage this hunk |
| `n` | Don’t stage this hunk |
| `q` | Quit patch mode |
| `a` | Stage this and all remaining hunks in the file |
| `d` | Skip this and all remaining hunks in the file |
| `s` | Split the hunk into smaller parts if possible |
| `e` | Manually edit the hunk before staging |
| `?` | Show help |

---

## 🧪 Example Workflow
1. Make multiple unrelated changes in a file.
2. Run:
   ```bash
   git add -p
   ```
3. Review each hunk Git presents.
4. Type `y` or `n` depending on whether you want to include that hunk.
5. Repeat for each change.

---

## 🎯 Use Cases
- Staging only feature-related code changes, leaving debug logs out.
- Committing