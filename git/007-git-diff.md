# Git Diff

## Overview

> `git diff` is a command used in Git to compare changes between different states of a repository. It helps track modifications, review unstaged or staged changes, and compare different commits, branches, or working directories.



## Usage

### 1. Show Unstaged Changes
```sh
$ git diff
```
This command displays the changes that have been made but not yet staged.

### 2. Show Staged Changes
```sh
$ git diff --staged
```
Displays the changes that have been staged but not yet committed.

### 3. Show Changes Between Commits
```sh
$ git diff COMMIT1 COMMIT2
```
Compares the differences between two commits.

### 4. Show Changes in a Specific File
```sh
$ git diff path/to/file
```
Displays differences in a specific file.

### 5. Show Differences Between Branches
```sh
$ git diff branch1..branch2
```
Compares the differences between two branches.

### 6. Show Word-Level Differences
```sh
$ git diff --word-diff
```
Displays differences at the word level instead of line level.

### 7. Show Summary of Changes
```sh
$ git diff --stat
```
Provides a summary of changed files and the number of insertions and deletions.

## Examples

### Example 1: Comparing Two Commits
```sh
$ git diff 123abc 456def
```
This command compares changes between commits `123abc` and `456def`.

### Example 2: Comparing a Branch with Main
```sh
$ git diff feature-branch main
```
Shows differences between `feature-branch` and `main`.
