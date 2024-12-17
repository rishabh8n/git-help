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

### 11. Merge a Branch into Main

To merge changes from a branch into the `main` branch, first switch to the `main` branch:

```sh
git checkout main
```

Then, use the `merge` command:

```sh
git merge <branch-name>
```

Example:

```sh
$ git checkout main
Switched to branch 'main'
$ git merge feature-branch
Updating 1a2b3c4..5d6e7f8
Fast-forward
 file.txt | 1 +
 1 file changed, 1 insertion(+)
```

If there are conflicts during the merge, Git will prompt you to resolve them before completing the merge.

### 12. Resolve Merge Conflicts

When you encounter a merge conflict, Git will mark the conflicted areas in the affected files. You need to manually resolve these conflicts by editing the files.

#### Steps to Resolve Merge Conflicts:

1. **Identify Conflicted Files**: Git will list the files with conflicts after a merge attempt.

   Example:

   ```sh
   $ git status
   On branch main
   You have unmerged paths.
     (fix conflicts and run "git commit")
     (use "git merge --abort" to abort the merge)

   Unmerged paths:
     (use "git add <file>..." to mark resolution)
     both modified:   file.txt
   ```

2. **Open Conflicted Files**: Open the files in your code editor. Conflicted areas will be marked like this:

   ```diff
   <<<<<<< HEAD
   Your changes
   =======
   Changes from the branch being merged
   >>>>>>> branch-name
   ```

3. **Resolve Conflicts**: Edit the file to resolve the conflicts. Remove the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`) and make the necessary changes.

4. **Stage Resolved Files**: After resolving the conflicts, stage the resolved files.

   ```sh
   git add <file>
   ```

   Example:

   ```sh
   $ git add file.txt
   ```

5. **Commit the Merge**: Finally, commit the merge to complete the process.

   ```sh
   git commit
   ```

   Example:

   ```sh
   $ git commit -m "Resolved merge conflicts"
   ```

If you want to abort the merge process, you can use:

```sh
git merge --abort
```

This will stop the merge and revert the repository to its previous state.

### 13. Rename a Branch

To rename the current branch, use:

```sh
git branch -m <new-branch-name>
```

Example:

```sh
$ git branch -m new-branch-name
```

To rename a different branch, use:

```sh
git branch -m <old-branch-name> <new-branch-name>
```

Example:

```sh
$ git branch -m old-branch-name new-branch-name
```

### 14. Delete a Branch

To delete a local branch, use:

```sh
git branch -d <branch-name>
```

Example:

```sh
$ git branch -d feature-branch
```

If the branch has not been merged, you can force delete it using:

```sh
git branch -D <branch-name>
```

Example:

```sh
$ git branch -D feature-branch
```

To delete a remote branch, use:

```sh
git push origin --delete <branch-name>
```

Example:

```sh
$ git push origin --delete feature-branch
```

### 15. View Differences Between Commits

To view the differences between commits, use:

```sh
git diff <commit1> <commit2>
```

Example:

```sh
$ git diff 1a2b3c4 5d6e7f8
```

To view the differences between the working directory and the staging area, use:

```sh
git diff
```

Example:

```sh
$ git diff
```

To view the differences between the staging area and the last commit, use:

```sh
git diff --staged
```

Example:

```sh
$ git diff --staged
```

To view the differences between two branches, use:

```sh
git diff <branch1> <branch2>
```

Example:

```sh
$ git diff main feature-branch
```

These commands help you see what changes have been made before committing them.

### 16. Stash Changes

To temporarily save changes that are not ready to be committed, use:

```sh
git stash
```

Example:

```sh
$ git stash
Saved working directory and index state WIP on main: 1a2b3c4 Initial commit
```

To list all stashes, use:

```sh
git stash list
```

Example:

```sh
$ git stash list
stash@{0}: WIP on main: 1a2b3c4 Initial commit
```

To apply the most recent stash, use:

```sh
git stash apply
```

Example:

```sh
$ git stash apply
```

To apply a specific stash, use:

```sh
git stash apply stash@{n}
```

Example:

```sh
$ git stash apply stash@{0}
```

To drop a specific stash, use:

```sh
git stash drop stash@{n}
```

Example:

```sh
$ git stash drop stash@{0}
Dropped stash@{0} (WIP on main: 1a2b3c4 Initial commit)
```

To clear all stashes, use:

```sh
git stash clear
```

Example:

```sh
$ git stash clear
```

To apply and remove the most recent stash, use:

```sh
git stash pop
```

Example:

```sh
$ git stash pop
```

### 17. Tagging

To create a new tag, use:

```sh
git tag <tag-name>
```

Example:

```sh
$ git tag v1.0
```

To create a new tag with a message, use:

```sh
git tag -a <tag-name> -m "tag message"
```

Example:

```sh
$ git tag -a v1.0 -m "Initial release"
```

To attach a tag to a specific commit, use:

```sh
git tag <tag-name> <commit-id>
```

Example:

```sh
$ git tag v1.0 1a2b3c4
```

To list all tags, use:

```sh
git tag
```

Example:

```sh
$ git tag
v1.0
```

To show information about a specific tag, use:

```sh
git show <tag-name>
```

Example:

```sh
$ git show v1.0
```

To push a tag to a remote repository, use:

```sh
git push origin <tag-name>
```

Example:

```sh
$ git push origin v1.0
```

To delete a local tag, use:

```sh
git tag -d <tag-name>
```

Example:

```sh
$ git tag -d v1.0
Deleted tag 'v1.0' (was 1a2b3c4)
```

To delete a remote tag, use:

```sh
git push origin --delete <tag-name>
```

Example:

```sh
$ git push origin --delete v1.0
```

### 18. Rebase

To rebase the current branch onto another branch, use:

```sh
git rebase <branch-name>
```

Example:

```sh
$ git rebase main
```

To interactively rebase, use:

```sh
git rebase -i <commit-id>
```

Example:

```sh
$ git rebase -i HEAD~3
```

To continue a rebase after resolving conflicts, use:

```sh
git rebase --continue
```

Example:

```sh
$ git rebase --continue
```

To abort a rebase, use:

```sh
git rebase --abort
```

Example:

```sh
$ git rebase --abort
```

### 19. Reflog

To view the reference logs, which record when the tips of branches and other references were updated, use:

```sh
git reflog
```

Example:

```sh
$ git reflog
```

To view the reflog for a specific branch, use:

```sh
git reflog <branch-name>
```

Example:

```sh
$ git reflog main
```

To delete a specific reflog entry, use:

```sh
git reflog delete <reflog-entry>
```

Example:

```sh
$ git reflog delete HEAD@{1}
```

To expire reflog entries older than a specific time, use:

```sh
git reflog expire --expire=<time> --all
```

Example:

```sh
$ git reflog expire --expire=30.days.ago --all
```

To clean up all reflog entries, use:

```sh
git reflog expire --expire=now --all
```

Example:

```sh
$ git reflog expire --expire=now --all
```

### 20. Git Reset

The `git reset` command is used to undo changes in your working directory and staging area. It can be used to unstage files, revert commits, and move the HEAD pointer to a previous commit.

#### 1. Unstage Files

To unstage a file that has been added to the staging area, use:

```sh
git reset <file>
```

Example:

```sh
$ git reset README.md
Unstaged changes after reset:
M	README.md
```

#### 2. Revert to a Previous Commit

To move the HEAD pointer and the current branch to a previous commit, use:

```sh
git reset <commit>
```

Example:

```sh
$ git reset 1a2b3c4
```

#### 3. Types of Reset

There are three types of reset operations: `--soft`, `--mixed`, and `--hard`.

- `--soft`: Moves the HEAD pointer to the specified commit, but leaves the staging area and working directory unchanged.

  ```sh
  git reset --soft <commit>
  ```

  Example:

  ```sh
  $ git reset --soft HEAD~1
  ```

- `--mixed` (default): Moves the HEAD pointer to the specified commit and resets the staging area, but leaves the working directory unchanged.

  ```sh
  git reset --mixed <commit>
  ```

  Example:

  ```sh
  $ git reset --mixed HEAD~1
  ```

- `--hard`: Moves the HEAD pointer to the specified commit and resets both the staging area and working directory to match the commit.

  ```sh
  git reset --hard <commit>
  ```

  Example:

  ```sh
  $ git reset --hard HEAD~1
  ```

#### 4. Reset to a Specific File

To reset a specific file in the working directory to match the latest commit, use:

```sh
git checkout HEAD -- <file>
```

Example:

```sh
$ git checkout HEAD -- README.md
```

#### 5. Reset to a Remote Branch

To reset the current branch to match a remote branch, use:

```sh
git reset --hard origin/<branch-name>
```

Example:

```sh
$ git reset --hard origin/main
```

#### 6. Reset to a Specific Commit and Keep Changes

To reset to a specific commit but keep the changes in the working directory, use:

```sh
git reset --keep <commit>
```

Example:

```sh
$ git reset --keep 1a2b3c4
```

Use `git reset` with caution, especially with the `--hard` option, as it can permanently delete changes from your working directory and staging area.

## Conclusion

These are some of the basic Git commands to get you started with version control. For more advanced usage, refer to the [official Git documentation](https://git-scm.com/doc).
