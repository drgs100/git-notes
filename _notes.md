# Git notes

## config

```git config --global --edit```

Always set name and email

```bash

git config --global user.name "your name"
git config --global user.email "your email"

```

Set up short cuts, you will never regret this.

```bash

git config --global alias.co checkout
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.br branch
git config --global alias.fh fetch

```

There are three different config files

```bash
git config --global
git config --system
git config --local
```

Find your configs

```bash
git config --list --show-origin     # shows where all your setting live
git config --[local/global] -e      # edit a config file in system editor
```

## add and commit

```bash

git add .                       # add all files
git commit                      # opens editor for commit message
git commit -m "add message"     # message short cut

```

Convention for commit messages (when using the editor). Summarize the commit on the first line in less than 50 characters, leave a blank line and give more detailed explanation. Use present tense. e.g

> Change the message displayed by hello.py
> - Update the sayHello() function to output the user's name
> - Change the sayGoodbye() function to a friendlier message

## branches (using br shortcut)

```bash

git br                          # list all available branches
git br <branch>                 # create new branch, does not co the branch
git br -m <newname>             # rename current branch
git br -m <oldname> <newname>   # rename any branch
git br -d <branch>              # safe delete specified branch but not if there are unmerged changes
git br -D <branch>              # force delete
git br -a                       # list all remote branches
git co -b <branch>              # create new branch and check it out

```

## Stashing

Stashing does not get pushed.

```bash

git stash pop       # reapply previously stashed changes
git stash apply     # reapplies changes and keeps in stash
git stash show      # show the changes between stashes
git stash pop       # reapply previously stashed changes
git stash apply     # reapplies changes and keeps in stash
git stash drop      # remove a single stash
git stash clear     # remove all stashes

```

Use ```apply``` when applying the same stashed changes across multiple branches.

By default stash ignores un-tracked and ignored files.

```bash

git stash -u    # include un-tracked files
git stash -a    # include all inc ignored files

```

### multiple stashes

```bash

git stash list              # show all stashes
git stash save "message"    # make life easier with message
git stash pop stash@{2}     # re-apply specific stash
git stash show              # view summary of diffs
git stash show -p           # view full diff of stash
git stash -p                # partial stashes, gets confusing

```

### Create branches from stashes

```bash

git stash branch <branch-name> stash@{1} # creates new branch and pops

```

### Clean up that stash!

```bash

git stash drop stash@{1}    # If you no longer need that stash
git stash clear             # Delete all stashes

```

## log

```bash

git reflog          # This is much more useful than log
git log --oneline   # Easy way to see all commits inc hash
git log -n <n>      # Show previous n commits

```

## checkout

```bash

git checkout master
git checkout <commit> <file>    # Checkout a file from previous commit
git checkout <commit>           # Checkout previous commit (moves HEAD)
git checkout HEAD <file>        # Checkout most recent version of file

```

## remotes

```bash

git clone <url>   # clone a remote repo, automatically creates a connection called origin

```

Clone - I don't quite have the hang of this yet. Currently instead of cloning I am using ```remote add``` then ```pull```.

```bash

git remote                                # list the remote connections to other repos
git remote -v                             # include urls
git remote add <name> <url>               # create new connection to remote repo 
git remote rm <name>                      # remove connection to named remote
git remote rename <old-name> <new name>   # rename remote

```

```bash

git fetch <remote>            # imports commits from remote repo into 'remote branches', giving a chance to review
git fetch <remote> <branch>   # fetches a specific branch
git branch -r                 # show remote branches
git pull <remote>             # run fetch and merge together
git pull --rebase <remote>    # using rebase instead

```

### pushing

This became more complicated, turns out one needs a bare repo when relying on a central repo. Then you need to 
set up an upstream remote.

```bash

git init --bare                                     # set up bare repo
git push [-u | --set-upstream] <remote> <branch>    # set upstream branch
git push <remote> <branch>                          # push changes up to a remote

```

## diff

Check the difference between two branches/hashes/commits. This gets much more complicated
but I've not got to the bottom of it yet.

```bash

git diff <target> <target>              # shows the changes in bash
git diff <target> <target> --name-only  # shows only the names of the changed files

```

## clean up

```bash

git gc          # cleanup unnecessary files and optimise local repo

```

## Tagging

```bash
git tag <tagname>                       # lightweight tag (convention - private)
git tag -a v1.4                         # annotated tag, contains metadata (convention - public)
git tag -a v1.4 -m "my version 1.4"     # with message

git tag     # list stored tags
```

## Articles

Some articles that might save your bacon.

[Git Catastrophes and Tips to Avoid Them](https://blog.risingstack.com/git-catastrophes-and-tips-to-avoid-them/) - contains a save if you commit to the wrong branch. I think VS uses something like this.

[Introduction to Git with Scott Chacon of GitHub](https://www.youtube.com/watch?v=ZDR433b0HJY) Not watched yet.

