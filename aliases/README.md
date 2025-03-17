## What are git aliases ?

> A Git alias is a shorthand for a Git command or series of commands. 

> By creating an alias, you can replace a lengthy command with a short and memorable abbreviation. This not only saves time but also reduces the risk of errors when typing commands.

## Why Use Git Aliases?

1. **`Efficiency`**: Save time by reducing the amount of typing needed.
2. **`Consistency`**: Ensure you use the same commands consistently across different projects.
3. **`Customization`**: Tailor your Git experience to suit your specific workflow.
4. **`Ease of Use`**: Simplify complex commands into straightforward ones.

## Types of Git Aliases

> A Git alias can be either local or global. A local alias is defined for a particular git repository whereas a global alias can be used in any repository. 

> If you create an alias inside a git repository without the global flag, then the alias will be local by default i.e. it can be used in the current repository only. Alias created with global flags can be used in any git repository.

## Creating Git Aliases

> Creating Git aliases is straightforward. You can set them up in your **`.gitconfig`** file or by using Git commands directly in the terminal.

### create Using Git Config

```sh
Syntax:  git config –global alias.<custom_command_name> <original_command Name> 
```

```sh
$ git config --global alias.co checkout
$ git config --global alias.br branch
$ git config --global alias.ci commit
$ git config --global alias.st status
$ git config --global alias.last 'log -1 HEAD'
$ git config --global alias.dog "log --all --decorate --oneline --graph"
```

> now we can test as below 

```sh 
$ git co              # use git co instead of git checkout
$ git ci              # use git ci instead of git commit
$ git st              # use git st instead of git status
$ git br              # use git br instead of git branch
```

### Edit git config file directly 

> for global config refer: **`$HOME/.gitconfig`**

> for local config refer: **`.git/config`**

```sh 
[user]
    name = my name
    email = me@example.com
[core]  
    editor = vi 
[alias]
    aa = add --all
    bv = branch -vv
    ba = branch -ra
    bd = branch -d
    ca = commit --amend
    cob = checkout -b
    cm = commit -a --amend -C HEAD
    ci = commit -a -v
    co = checkout
    di = diff
    mm = merge --no-ff
    st = status --short --branch
    tg = tag -a 
    pu = push --tags
    un = reset --hard HEAD  
    uh = reset --hard HEAD^
```

### more aliases 
```sh 
# one-line log
l = log --pretty=format:"%C(yellow)%h\\ %ad%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate --date=short
ll = log --pretty=format:"%C(yellow)%h%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate --numstat
ld = log --pretty=format:"%C(yellow)%h\\ %C(green)%ad%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate --date=short --graph
ls = log --pretty=format:"%C(green)%h\\ %C(yellow)[%ad]%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate --date=relative

a = add
ap = add -p
c = commit --verbose
ca = commit -a --verbose
cm = commit -m
cam = commit -a -m
m = commit --amend --verbose

d = diff
ds = diff --stat
dc = diff --cached

s = status -s

# list branches sorted by last modified
b = "!git for-each-ref --sort='-authordate' --format='%(authordate)%09%(objectname:short)%09%(refname)' refs/heads | sed -e 's-refs/heads/--'"

# list aliases
la = "!git config -l | grep alias | cut -c 7-"
```