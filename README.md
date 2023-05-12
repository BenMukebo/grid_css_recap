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

- Undo Add & Commit

```bash
$ git reset HEAD~ # undo last commit but keep changes OR 
$ git reset HEAD~2
$ git revert HEAD # Create a new commit that undoes all of the changes made in the most recent commit
$ git revert <commit_hash> # Create a new commit that undoes all of the changes made in <commit_hash>, then apply it to the current branch.
```
- Check commit history

```bash
$ git reflog # Display what happend inside the commit history
$ git log --graph --decorate --oneline # Display what happend inside the commit history
$ git log -S "git checkout -b" # Search this text inside all my commit to see where this text came from or modify are showing up
```
- Save changes

```bash 
- git stash # Save changes to a stash so you can work on something else, and then come back and re-apply them later on.
- git stash list # List all stashes
- git stash apply # Apply the most recent stash to the current branch
- git stash pop # Apply the most recent stash to the current branch, and then delete it
- git stash apply stash@{2} # Apply the second most recent stash to the current branch
- git stash drop # Delete the most recent stash
- git stash drop stash@{2} # Delete the second most recent stash
- git stash clear # Delete all stashes
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