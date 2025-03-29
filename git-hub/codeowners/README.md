## CodeOwners ? 
> In the context of software development and code management, "**code owners**" are `individuals` or `teams` responsible for specific parts of a codebase.
> 

## Purpose
> Code owners ensure that the right people, with expertise in the relevant code, are involved in the review process, promoting quality, style, and functionality standards. 

> defined in a **`CODEOWNERS file`**, who are automatically requested for review when changes to their area are proposed.

## How it works

1. A **`CODEOWNERS file`** is used to map code paths (files or directories) to specific users or teams. 

2. When a pull request (or merge request) modifies code within a code owner's area, they are automatically requested to review the changes. 

3. This streamlines the review process and ensures that changes are vetted by the right people. 

## Benefits

1. **`Improved code quality:`** By involving experts in the review process, code owners help ensure that changes meet the required standards. 

2. **`Enhanced security:`** Code owners can help identify potential security vulnerabilities in their areas of responsibility. 

3. **`Streamlined reviews:`** Automatically requesting reviews from the right people saves time and effort. 

4. **`Better knowledge sharing:`** Code owners become the go-to people for questions and issues related to their code areas. 


## CODEOWNERS Syntax & Example

> A CODEOWNERS file uses a pattern that follows most of the same rules used in `gitignore` files. The pattern is followed by one or more GitHub usernames or team names using the standard `@username` or `@org/team-name` format. 

> Important: Users and teams must have explicit write access to the repository, even if the team's members already have access.

> If you want to match two or more code owners with the same pattern, all the code owners must be on the same line. If the code owners are not on the same line, the pattern matches only the last mentioned code owner.

> `CODEOWNERS paths are case sensitive`, because GitHub uses a case sensitive file system. Since CODEOWNERS are evaluated by GitHub, even systems that are case insensitive (for example, macOS) must use paths and files that are cased correctly in the CODEOWNERS file.

> If any line in your CODEOWNERS file contains invalid syntax, that line will be skipped. When you navigate to the CODEOWNERS file in your repository, you can see any errors highlighted 

#### Example
```txt
# This is a comment.
# Each line is a file pattern followed by one or more owners.

# These owners will be the default owners for everything in
# the repo. Unless a later match takes precedence,
# @global-owner1 and @global-owner2 will be requested for
# review when someone opens a pull request.
*       @global-owner1 @global-owner2

# Order is important; the last matching pattern takes the most
# precedence. When someone opens a pull request that only
# modifies JS files, only @js-owner and not the global
# owner(s) will be requested for a review.
*.js    @js-owner #This is an inline comment.

# You can also use email addresses if you prefer. They'll be
# used to look up users just like we do for commit author
# emails.
*.go docs@example.com

# Teams can be specified as code owners as well. Teams should
# be identified in the format @org/team-name. Teams must have
# explicit write access to the repository. In this example,
# the octocats team in the octo-org organization owns all .txt files.
*.txt @octo-org/octocats

# In this example, @doctocat owns any files in the build/logs
# directory at the root of the repository and any of its
# subdirectories.
/build/logs/ @doctocat

# The `docs/*` pattern will match files like
# `docs/getting-started.md` but not further nested files like
# `docs/build-app/troubleshooting.md`.
docs/* docs@example.com

# In this example, @octocat owns any file in an apps directory
# anywhere in your repository.
apps/ @octocat

# In this example, @doctocat owns any file in the `/docs`
# directory in the root of your repository and any of its
# subdirectories.
/docs/ @doctocat

# In this example, any change inside the `/scripts` directory
# will require approval from @doctocat or @octocat.
/scripts/ @doctocat @octocat

# In this example, @octocat owns any file in a `/logs` directory such as
# `/build/logs`, `/scripts/logs`, and `/deeply/nested/logs`. Any changes
# in a `/logs` directory will require approval from @octocat.
**/logs @octocat

# In this example, @octocat owns any file in the `/apps`
# directory in the root of your repository except for the `/apps/github`
# subdirectory, as its owners are left empty. Without an owner, changes
# to `apps/github` can be made with the approval of any user who has
# write access to the repository.
/apps/ @octocat
/apps/github

# In this example, @octocat owns any file in the `/apps`
# directory in the root of your repository except for the `/apps/github`
# subdirectory, as this subdirectory has its own owner @doctocat
/apps/ @octocat
/apps/github @doctocat
```
