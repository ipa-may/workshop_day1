# Basic Git Commands

Git is a version control system. It helps you track changes in files, work on a project over time, and collaborate with other people.

## Why use Git?

With Git you can:

- save the history of your project
- go back to older versions
- see what changed
- work together on the same code

## Important ideas

`Repository:` A Git project folder.

`Commit:` A saved snapshot of your work.

`Branch:` A separate line of development.

`Remote:` A version of the repository stored on a server such as GitHub.

## Typical Git workflow

1. Check what changed
2. Add the files you want to save
3. Create a commit with a message
4. Push the commit to the remote repository

## Basic commands

`git clone`

Copies an existing repository to your computer.

Example:

```bash
git clone https://github.com/ipa-may/workshop_day1.git
```

#

`git status`

Shows the current state of the repository.

It tells you:

- which branch you are on
- which files changed
- which files are staged
- which files are not tracked yet

Example:

```bash
git status
```

`git add`

Stages files for the next commit.

Examples:

```bash
git add my_file.txt
git add .
```

`git commit`

Creates a snapshot of the staged changes.

Example:

```bash
git commit -m "Add workshop notes"
```

The commit message should explain what changed.

`git log`

Shows the commit history.

Example:

```bash
git log
```

Useful short version:

```bash
git log --oneline
```

`git diff`

Shows the changes that were made.

Example:

```bash
git diff
```

To see staged changes:

```bash
git diff --staged
```

`git pull`

Downloads new changes from the remote repository and updates your local branch.

Example:

```bash
git pull
```

`git push`

Uploads your local commits to the remote repository.

Example:

```bash
git push
```

`git branch`

Shows branches in the repository.

Example:

```bash
git branch
```

`git checkout`

Switches to another branch.

Example:

```bash
git checkout main
```

## Simple example

```bash
git status
git add notes.txt
git commit -m "Update notes"
git push
```

## Good habits

- run `git status` often
- write short and clear commit messages
- commit small logical changes
- pull before you start working if others may have changed the repository

## Tip

A common way to think about Git is:

- working directory: your current files
- staging area: the files prepared for the next commit
- repository history: the saved commits

For the workshop task, see [EXERCICE.md](./EXERCICE.md).


## HTTPS vs SSH

Git repositories are often accessed in two ways:

`HTTPS`

Example:

```bash
https://github.com/ipa-may/workshop_day1.git
```

`SSH`

Example:

```bash
git@github.com:ipa-may/workshop_day1.git
```

Main difference:

- `HTTPS` uses a normal web-style URL
- `SSH` uses your SSH key for authentication

When to use `HTTPS`:

- easy to start with
- good for first-time users
- useful when you do not have an SSH key configured

When to use `SSH`:

- convenient for regular Git users
- useful when you push often
- avoids typing username or password prompts in many setups


# Changing the remote URL

Sometimes a repository is cloned with `HTTPS`, but later you want to use `SSH` instead.

You can change the remote named `origin` with:

```bash
git remote set-url origin git@github.com:ipa-may/workshop_day1.git
```

This tells Git to use the SSH address for the remote called `origin`.

To check the configured remotes, run:

```bash
git remote -v
```

Example output:

```text
origin  git@github.com:ipa-may/workshop_day1.git (fetch)
origin  git@github.com:ipa-may/workshop_day1.git (push)
```

This is useful if:

- you first cloned with `HTTPS`
- you later configured an SSH key
- you want to push using `SSH`
