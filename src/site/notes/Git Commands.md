---
{"dg-publish":true,"permalink":"/git-commands/","title":"Git Commands","created":"2021-09-08T20:50:01","updated":"2023-04-13T13:53:42"}
---

> [!meta]-
> sup:: [[Git\|Git]]  
> state:: done

# Git Commands

## Add

- `git add -A` stages **all changes**
    - = `git add .` + `git add -u`
- `git add .` stages new files and modifications, ~~without deletions~~ (on the current directory and its subdirectories)
    - <span class="alt-check alt-check-rmk">For Git >= 2.0, `git add .` will add deletions! Use flag `--ignore-removal` to ignore deletion</span>
    - <span class="alt-check alt-check-rmk">Therefore, `git add -A` is redundant for Git >= 2.0</span>
- `git add -u` stages modifications and deletions, **without new files**

## Combine add and commit

```bash
git commit -am "commit message"
```

is equal to

```bash
git add -u
git commit -m "commit message"
```

## Alias

```bash
git config --global alias.ac "commit -am"
git ac "commit message"
```

is equal to

```bash
git commit -am "commit message"
```

## Branch

```bash
# Create a branch
git branch -M main
# Rename a branch
git branch -M master main
```

## Log in Terminal

To get better log info like in the GUI

```bash
git log --graph --oneline --decorate
```

## Stash

`stash` store your changes without commit, remove them now, and pop out when you need them again

```bash
# Store all your changes without commit, and hide them
git stash
# Pop out your hidden changes
git stash pop
# Stash your changes with a given name
git stash save "your stash name"
# Show all your stashes
git stash list
# Apply a certain stash in the list
git stash apply index
```

## Ignore

To ignore some files or directories, add them to the `.gitignore` file. However, this will not work for files/dirs that have already been tracking. To remove those files/dirs from **git tracking** (not delete them), use

```bash
git rm -r --cached path_to_file_or_dir
```

## New Branch

```sh
# Create a new branch called new_branch
git branch new_branch
# Checkout (switch) to the new branch
git checkout new_branch
```

These two commands have a shorthand:

```sh
git checkout -b new_branch
```

## Discard Branch

When a branch is pulled/merged into main, it is no longer needed.

```sh
git branch -d patch # delete branch
git fetch -p        # stop tracking obsolete remote branches (prune)
```

## Remotes

```sh
# View the remotes
git remote -v
# Add a remote called origin
git remote add origin git@github.com:zcysxy/repo.git
# Change the url of the remote origin
git remote set-url origin https://github.com/zcysxy/repo.git
```

When forking an other's repo, remember to add the other's repo as an **upstream repo**.

```sh
git remote add upstream git@github.com:yiyi/repo.git
```

> [!rmk] Forking and Making Pull Requests Best Practice
> 1. Set the original repo as the upstream repo.
> 2. Switch to a new branch before making any changes.
> 3. Make a pull request from a new branch other than `main`/`master`.
> 4. After the pull request is merged into the original repo, pull it into your own `main`/`master` branch.
> 5. Delete the obsolete branch. `git branch -D obsolete-branch`

## Discard Changes

```bash
# Restore several files
git restore file1 file2 file3

# Restore all
git restore .
```

## Get Files from Other Branches

To get files from other branches, you can either use `checkout` command or `restore` command.

```bash
# main branch
git checkout other_branch -- file1 file2
# or
git restore --source other_branch -- file1 file2
```

## Show Tracked Files

List all the files currently being tracked under the branch `master`

```sh
git ls-tree -r master --name-only
```

## Remote Status

To show what's going on in the remote branches, you need to fetch/update them first, then compare the differences.

```sh
# Method 1
git fetch origin
git diff origin/master
git merge origin/master

# Method2
git remote update
git status
```

## List Files

### ls-files

```shell
git ls-files # Show information about files in the index and the working tree
    [-c|--cached] [-d|--deleted] [-o|--others] [-i|--|ignored]
    [-s|--stage] [-u|--unmerged] [-k|--|killed] [-m|--modified]
    [--directory [--no-empty-directory]] [--eol]
    [--deduplicate]
    [-x <pattern>|--exclude=<pattern>]
    [-X <file>|--exclude-from=<file>]
    [--exclude-per-directory=<file>]
    [--exclude-standard]
    [--error-unmatch] [--with-tree=<tree-ish>]
    [--full-name] [--recurse-submodules]
    [--abbrev[=<n>]] [--] [<file>…​]
```

### ls-tree

```shell
git ls-tree -r main --name-only
```

> [!tip] `ls-tree` > `ls-files`
> `ls-tree` is better than `ls-files` because `ls-files` may differ from the `--work-tree`.

## Garbage Collection

To "collect the garbage" in the `.git` folder and reduce its size, use

```shell
git gc
# or spend more time optimizing using
git gc --aggressive
```

This command actually executes a bundle of other internal subcommands like `git prune`, `git repack`, `git pack` and `git rerere`. These subcommands identify any Git objects that are outside the threshold levels set from the `git gc` configuration, and then compress, or prune them accordingly.

## Global `.gitignore`

You can create a global `.gitignore` file to ignore files for all git repositories. When you created that file, run the following command

```shell
git config --global core.excludesfile <path_to_your_gitignore_global>
```

## Separate Git Directory

Sometimes, you don't want the `.git` directory to be in the same directory as the working tree (for example, to prevent sync issues).

```shell
cd ~/work/dir # working dir
git init –separate-git-dir ~/work/dir.git # git dir in the parent dir
```

## Merge Changes from Another Branch

```shell
# In branch main
git merge patch_branch
# or merge from a specific commit
git cherry-pick commit-hash
```

## Compare Current and Last Version

```shell
# HEAD~n is the nth generation ancestor of the named commit object (HEAD here)
git diff HEAD~1 HEAD
# Shortcuts
git diff HEAD~ HEAD
git diff HEAD~
git diff @~ # @ is an alias for HEAD
git show # doesn't work for merge commit
```
