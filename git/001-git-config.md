# git config

## Introduction

> **git config is a command in Git that allows users to configure settings for Git repositories. It helps manage user identity, default behaviors, and various Git features at different levels:**

	1.	System-wide (--system) – Affects all users on the machine (stored in /etc/gitconfig or C:\Program Files\Git\etc\gitconfig on Windows).
	2.	Global (--global) – Applies to a single user across all repositories (stored in ~/.gitconfig or C:\Users\YourUsername\.gitconfig).
	3.	Local (--local) – Affects only a specific Git repository (stored in .git/config inside the repository).

## Step 1: Check Existing Configuration
Before making changes, check the current Git configuration:
```sh
git config --list
```
Or, to see a specific configuration level:
```sh
# System-wide configuration
git config --system --list

# User-level (global) configuration
git config --global --list

# Repository-specific (local) configuration
git config --local --list
```

## Step 2: Set User Identity
Set your name and email, which are required for commits:
```sh
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```
To verify:
```sh
git config --global user.name
git config --global user.email
```

## Step 3: Configure Default Editor
To set the default text editor for Git commit messages:
```sh
git config --global core.editor "vim"
```
You can replace `vim` with `nano`, `code` (VS Code), or any preferred editor.

## Step 4: Configure Line Endings (Windows Users)
For Windows users to avoid line ending issues:
```sh
git config --global core.autocrlf true
```
For macOS/Linux:
```sh
git config --global core.autocrlf input
```

## Step 5: Set Default Branch Name
Change the default branch name for new repositories:
```sh
git config --global init.defaultBranch main
```

## Step 6: Configure Aliases
Git aliases help shorten commonly used commands. Example:
```sh
git config --global alias.st status
```
Now, you can use `git st` instead of `git status`.

## Step 7: Configure Credential Caching
To store credentials temporarily:
```sh
git config --global credential.helper cache
```
To store credentials permanently (Mac/Linux):
```sh
git config --global credential.helper osxkeychain
```
For Windows:
```sh
git config --global credential.helper wincred
```

## Step 8: Remove or Unset a Configuration
To remove a setting:
```sh
git config --global --unset user.email
```
To remove all global configurations:
```sh
rm ~/.gitconfig
```

## Step 9: Edit Configuration Files Directly
You can manually edit the configuration files using:
```sh
git config --global --edit
```
This opens the global config file in your default editor.

## Conclusion
Using `git config`, you can customize Git to suit your workflow. Always verify your settings with `git config --list` to ensure correctness.