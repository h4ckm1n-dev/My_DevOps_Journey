# Git Cheat-Sheet

Git is a distributed version control system used for tracking changes in source code during software development. It provides a powerful set of commands to manage and collaborate on projects.

Documentation: [Git Documentation](https://git-scm.com/doc)

## Configuration

COMMAND | DESCRIPTION
---|---
`git config --global user.name "Your Name"` | Set your name for all repositories
`git config --global user.email "your_email@example.com"` | Set your email for all repositories
`git config --global core.editor <editor>` | Set your preferred text editor
`git config --list` | List all configuration settings

## Creating and Cloning Repositories

COMMAND | DESCRIPTION
---|---
`git init` | Initialize a new local repository
`git clone <repository>` | Clone a remote repository to your local machine

## Basic Workflow

COMMAND | DESCRIPTION
---|---
`git status` | Show the status of the current repository
`git add <file>` | Add a file to the staging area
`git add .` | Add all modified files to the staging area
`git commit -m "Commit message"` | Commit changes with a descriptive message
`git commit -a -m "Commit message"` | Stage and commit all changes in one command
`git diff` | Show changes between the working directory and the staging area
`git diff --staged` | Show changes between the staging area and the last commit
`git log` | Show commit history
`git log --oneline` | Show compact commit history
`git show <commit>` | Show details of a specific commit

## Branches

COMMAND | DESCRIPTION
---|---
`git branch` | List all branches
`git branch <branchname>` | Create a new branch
`git checkout <branchname>` | Switch to an existing branch
`git checkout -b <branchname>` | Create a new branch and switch to it
`git merge <branchname>` | Merge a branch into the current branch
`git branch -d <branchname>` | Delete a branch

## Remote Repositories

COMMAND | DESCRIPTION
---|---
`git remote add <name> <url>` | Add a remote repository
`git remote -v` | List all remote repositories
`git pull <remote> <branch>` | Fetch and merge changes from a remote repository
`git push <remote> <branch>` | Push local changes to a remote repository
`git clone <repository>` | Clone a remote repository to your local machine

## Undoing Changes

COMMAND | DESCRIPTION
---|---
`git checkout -- <file>` | Discard changes in a file
`git reset HEAD <file>` | Unstage a file
`git revert <commit>` | Create a new commit that undoes the changes of a specific commit
`git reset --hard <commit>` | Discard all changes and move to a specific commit

## Collaboration

COMMAND | DESCRIPTION
---|---
`git fetch <remote>` | Download changes from a remote repository
`git merge <remote>/<branch>` | Merge changes from a remote branch into the current branch
`git push <remote> <branch>` | Push local changes to a remote repository
`git pull <remote> <branch>` | Fetch and merge changes from a remote repository
`git branch -r` | List remote branches
`git branch -a` | List all local and remote branches

