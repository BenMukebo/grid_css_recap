# General recap

## grid_css_recap

## Git Command
> Git is a Distributed Version Vontrol System VCS. 
  The thing are stored in the form of Snapshot

- Branches:

```bash
$ git branch # list all local branches
$ git branch -a # list all local and remote branches
$ git branch <branch_name> # create new branch
$ git swich <branch_name> # switch to branch git-command
$ git checkout -b <branch_name> # create and switch to branch
$ git checkout <branch_name> # switch to branch
```

- Add & Commit
  
```bash
$ git add <file_name> # add file to staging area
$ git add . # only add all file from current directory to staging area
$ git add -A # add all files to staging area
$ git commit -m "commit message" # commit staged files
$ git commit -a -m "commit message" # add and commit all files but it never work for new files OR
$ git commit -am "commit message" 
```

- Undo git Add command before commit

```bash
$ git reset <file_name> # removes the changes made to the file since the last commit and resets it to the state of the last commit.
$ git reset # unstage all changes in the entire repository.
$ git restore --staged <file_name> # is considered the newer and recommended command.
  # The --staged option or flag tells Git to unstage the file, moving them from the staging area back to the working directory how it was before git add was run.
  # The changes are kept as modifications in the file, allowing you to make further adjustments before committing.
$ git restore --staged # unstage all changes in the entire repository.
$ git restore <file_name> # does not unstage changes but discard changes in a file and restore it to the state of the last commit.
  # It removes any modifications made to the file in the working directory and replaces it with the version from the last commit but,
  # unlike, it does not move the file from the staging area to the working directory.
  # better to use it If you have unstaged changes in a file
$ git restore # discard all changes in the entire repository
$ git rm --cached <file_name> # used to remove a file from the Git repository's index (staging area) without deleting it from the working directory.
  # meaning Git will no longer track changes to that file. Is useful when you want to stop tracking a file that was previously staged for commit.
$ git reset --hard # undo all git add and git commit Note: ovid using this command
```
- Undo git Commit command

```bash
$ git reset HEAD~ # undo last commit but keep changes OR 
$ git reset HEAD~2 # undo last 2 commits but keep changes
$ git revert HEAD # Create a new commit that undoes all of the changes made in the most recent commit
$ git revert <commit_hash> # Create a new commit that undoes all of the changes made in <commit_hash>, then apply it to the current branch.
```

- To undo a git reset HEAD~ command

```bash
$ git reflog # Find the commit hash of the commit you want to go back to

=> 670a8e2 HEAD@{0}: reset: moving to HEAD~
=> 4a27b87 HEAD@{1}: commit: Your previous commit message
=> 5d678b6 HEAD@{2}: commit: Your older commit message
# The most recent entry at the top (HEAD@{0}) should indicate the result of the git reset HEAD~ command.
# Identify the commit you want to restore, which should be the commit before the reset. (4a27b87)
# To undo the reset and move your branch pointer back to the desired commit:

$ git reset git reset HEAD@{1} # Reset to the commit hash you want to go back to
```

- Check commit history

```bash
$ git reflog # Display what happend inside the commit history
$ git log --graph --decorate --oneline # Display what happend inside the commit history
$ git log -S "git checkout -b" # Search this text inside all my commit to see where this text came from or modify are showing up
```
- Save changes

```bash 
$ git stash # Save changes to a stash so you can work on something else, and then come back and re-apply them later on.
$ git stash list # List all stashes
$ git stash pop # Apply the most recent stash to the current branch, and then delete it
$ git stash pop stash@{2} # Apply the second most recent stash to the current branch
$ git stash apply # Apply the most recent stash to the current branch
$ git stash apply stash@{2} # Apply the second most recent stash to the current branch
$ git stash drop # Delete the most recent stash
$ git stash drop stash@{2} # Delete the second most recent stash
$ git stash clear # Delete all stashes
```

- Hunting for a commit that introduced a bug

```bash
$ git bisect start # Start the bisect process
$ git bisect bad # Tell git that the current commit is bad
$ git bisect good <commit hash> # Tell git that a commit is good

# Git will now checkout a commit in the middle of the range you specified. Test your code and determine if the commit is good or bad. If it is good, run git bisect good. If it is bad, run git bisect bad. Git will then checkout another commit in the middle of the range. Repeat this process until git tells you that it has found the first bad commit.

$ git bisect bad # Tell git that the current commit is bad as well
$ git bisect good # Tell git that a commit is good

$ git bisect reset # End the bisect process and return to normal
``` 