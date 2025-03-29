# Git Tag

> Git tags are used to mark specific points in a repository's history, typically to indicate releases. This guide provides a step-by-step demonstration of how to use `git tag`.

## Prerequisites

Make sure you have:
- Git installed (`git --version` to check)
- A Git repository initialized (`git init` if not already done)
- OR clone an existing repository 


## Step 1: Check Existing Tags
```sh
git clone https://github.com/kubernetes/website
cd website
git tag
```
This command lists all existing tags in the repository.

## Step 2: Create an Annotated Tag
```sh
git tag -a v1.0 -m "Version 1.0 release"
```
This creates an annotated tag `v1.0` with a message describing the tag.

## Step 3: Create a Lightweight Tag
```sh
git tag v1.1
```
This creates a lightweight tag `v1.1`, which is just a pointer to a commit without extra metadata.

## Step 4: View Tag Details
```sh
git show v1.0
```
This displays details about the `v1.0` tag, including the commit message and metadata.

## Step 5: Push Tags to Remote Repository
```sh
git push origin v1.0
```
This pushes the `v1.0` tag to the remote repository.

To push all tags:
```sh
git push origin --tags
```

## Step 6: Checkout a Tag
```sh
git checkout v1.0
```
This checks out the repository at the tagged version.

For a new branch from a tag:
```sh
git checkout -b new-branch v1.0
```

## Step 7: Delete a Tag
- **Local deletion**:
  ```sh
  git tag -d v1.0
  ```
- **Remote deletion**:
  ```sh
  git push --delete origin v1.0
  ```

## Conclusion
Git tags are useful for versioning and release management. Use annotated tags for releases and lightweight tags for quick references. Happy coding!