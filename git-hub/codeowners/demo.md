# GitHub CODEOWNERS Demo

## Introduction
The `CODEOWNERS` file in a GitHub repository allows you to specify default reviewers for changes to specific files or directories. This ensures that the right people review critical changes before they are merged.

## Prerequisites
- A GitHub repository
- Repository admin or write access

## Step 1: Create a CODEOWNERS File
1. Navigate to your repository on GitHub.
2. Go to the `main` branch (or any branch where you want CODEOWNERS to apply).
3. Open the `.github/` directory. If it doesn’t exist, create it.
4. Inside `.github/`, create a new file named `CODEOWNERS`.

**Screenshot Placeholder:** _Add a screenshot showing the file creation process_

## Step 2: Define Code Owners
Edit the `CODEOWNERS` file and add rules in the following format:

```plaintext
# CODEOWNERS file format:
# Each line contains a file pattern followed by one or more GitHub usernames or teams.

# Example: Assign ownership of all files to @alice
* @nareshwart

# Assign ownership of backend code to a team
backend/ @org/team1

# Assign ownership of frontend files to multiple users
frontend/ @user1 @user2

# Assign ownership of a specific file
README.md @user1
```

**Screenshot Placeholder:** _Add a screenshot showing an example CODEOWNERS file_

## Step 3: Commit and Push the CODEOWNERS File
After defining ownership rules:
```sh
git add .github/CODEOWNERS
git commit -m "Add CODEOWNERS file"
git push origin main
```

## Step 4: Verify Code Owners in a Pull Request
1. Create a new pull request that modifies files covered by `CODEOWNERS`.
2. GitHub will automatically request reviews from the specified owners.

**Screenshot Placeholder:** _Add a screenshot showing auto-assigned reviewers in a PR_

## Additional Notes
- `CODEOWNERS` applies only to protected branches.
- Users must have **write access** to be assigned as code owners.
- Teams must be mentioned using the format `@org/team-name`.

## Conclusion
Using a `CODEOWNERS` file ensures that changes are reviewed by the appropriate team members, improving code quality and accountability. 🚀
