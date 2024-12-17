# Git Commands Cheat Sheet

## Introduction

This document provides a quick reference guide for some of the most commonly used Git commands.

## Git Config

### Set User Name

```sh
git config --global user.name "Your Name"
```

### Set User Email

```sh
git config --global user.email "you@example.com"
```

### Change Default Branch to Main

To change the default branch name to `main` for new repositories, use the following command:

```sh
git config --global init.defaultBranch main
```

### Set Default Code Editor for Commits to VSCode

To set Visual Studio Code as the default editor for Git commit messages, use the following command:

```sh
git config --global core.editor "code --wait"
```

These configurations are stored in the `.gitconfig` file in your home directory and are used for all your Git repositories.

## Git Commands

### 1. Initialize a New Repository

To create a new Git repository, use the following command:

```sh
git init
```

Example:

```sh
$ git init
Initialized empty Git repository in /path/to/repo/.git/
```

### 2. Check the Status of Your Repository

To check the status of your files in the working directory and staging area, use:

```sh
git status
```

Example:

```sh
$ git status
On branch master
No commits yet

Untracked files:
    (use "git add <file>..." to include in what will be committed)
        README.md

nothing added to commit but untracked files present (use "git add" to track)
```

### 3. Add Files to the Staging Area

To add files to the staging area, use:

```sh
git add <file>
```

Example:

```sh
$ git add README.md
```

### 4. Commit Changes

To commit the staged changes to the repository, use:

```sh
git commit -m "commit message"
```

Example:

```sh
$ git commit -m "Initial commit"
[master (root-commit) 1a2b3c4] Initial commit
 1 file changed, 1 insertion(+)
 create mode 100644 README.md
```

### 5. Remove Files from the Staging Area

To remove files from the staging area, use:

```sh
git reset <file>
```

Example:

```sh
$ git reset README.md
Unstaged changes after reset:
M	README.md
```

### 6. View Commit History

To view the commit history of your repository, use:

```sh
git log
```

Example:

```sh
$ git log
commit 1a2b3c4
Author: Your Name <you@example.com>
Date:   Mon Oct 2 12:34:56 2023 +0000

    Initial commit
```

#### Basic Flags

- `--oneline`: Show each commit on a single line.
- `--graph`: Display an ASCII graph of the branch and merge history.
- `--decorate`: Add names of branches or tags of commits shown.

Example with flags:

```sh
$ git log --oneline --graph --decorate
* 1a2b3c4 (HEAD -> master) Initial commit
```

### 7. View Current Branch

To view the branch you are currently on, use:

```sh
git branch
```

Example:

```sh
$ git branch
* master
```

### 8. Create a New Branch

To create a new branch, use:

```sh
git branch <branch-name>
```

Example:

```sh
$ git branch feature-branch
```

### 9. Switch to a Branch

To switch to an existing branch, use:

```sh
git checkout <branch-name>
```

Example:

```sh
$ git checkout feature-branch
Switched to branch 'feature-branch'
```

### 10. Create and Switch to a New Branch

To create a new branch and switch to it immediately, use:

```sh
git checkout -b <branch-name>
```

Example:

```sh
$ git checkout -b new-feature
Switched to a new branch 'new-feature'
```

## Conclusion

These are some of the basic Git commands to get you started with version control. For more advanced usage, refer to the [official Git documentation](https://git-scm.com/doc).
