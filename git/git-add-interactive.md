# git `add -i`

* The `git add -i` (or `git add --interactive`) command offers a powerful, menu-driven interface to selectively stage changes in Git. 

* It's especially useful for staging only parts of your working directory or for reviewing changes before staging.

* git add --interactive launches an interactive terminal UI that helps you choose exactly what to stage for your next commit.

## Why Use `git add -i`?
- Selectively stage changes without using external tools
- Ideal for organizing commits
- Easier to navigate than manual `git add -p`

## Launching Interactive Mode
```bash
git add -i
```
This command opens an interactive prompt with several options.

## Main Menu Options
When you run `git add -i`, you'll see a menu like this:
```
status        [s]  show paths with changes
update        [u]  add working tree state to the index
revert        [r]  revert unstaged changes
add untracked [a]  add contents of untracked files to the index
patch         [p]  pick hunks and add them to the index
diff          [d]  view diff between index and work tree
quit          [q]  quit; don't apply
help          [h]  show help
```

## Common Use Cases and Examples

### 1. Stage Changes Interactively (`update`)
```bash
# From the interactive menu, type:
u
```
- Lists files with modifications.
- Lets you select which files to stage.

### 2. Add Untracked Files (`add untracked`)
```bash
# From the interactive menu, type:
a
```
- Displays untracked files.
- Choose files to add to the index.

### 3. Stage Specific Hunks (`patch`)
```bash
# From the interactive menu, type:
p
```
- Similar to `git add -p`.
- Allows you to review and stage code hunk by hunk.

### 4. View Changes Before Staging (`diff`)
```bash
# From the interactive menu, type:
d
```
- View differences between your working directory and the index.

### 5. Revert Unstaged Changes (`revert`)
```bash
# From the interactive menu, type:
r
```
- Discard changes in your working directory that haven't been staged yet.

### 6. Quit the Interface (`quit`)
```bash
# From the interactive menu, type:
q
```
- Exit without making any changes.

## Tips
- Use this command when preparing clean, logical commits.
- Ideal for splitting unrelated changes into separate commits.

## Alternate: `git add -p` vs `git add -i`
- `git add -p` is for staging individual hunks in a streamlined way.
- `git add -i` is more comprehensive and menu-driven.

## Conclusion
`git add -i` is a great tool for developers who want granular control over what they stage in Git. Whether you're reviewing code, cleaning up commits, or working with multiple changes at once, interactive staging gives you power and flexibility.
