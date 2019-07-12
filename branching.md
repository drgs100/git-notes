# Branching with Daisy

## Branching process

About to start working on a new work item?

1. Pull master branch down from DevOps (origin) `git pull origin master`
2. Create and checkout a new branch `git checkout -b "new-branch"` (see below for naming)
3. Get some work done
4. Make a commit `git commit -m "Commit message #234"` (see below for commit message)
5. Push branch to origin `git push origin new-branch`
6. Repeat steps 3-5*.
7. When feature or bug is complete make a pull request in DevOps
8. Start all over again with new work item

*It is also worth making regular merges from master

- `git checkout master`
- `git pull origin master`
- `git checkout new-branch`
- `git merge master`

## Naming convention for branches

Type of work item (feature or bug) - work item number - short description.

- Feature, `feat/daisy-1234-short-description`
- Bug, `bug/daisy-234-short-description`

## Commit message

A good commit message should give the context of the change, other tools can show the change.

Finish your commit message with the work item number for DevOps to [create a bidirectional link](https://stackoverflow.com/questions/54577475/azuredevops-link-git-commit-or-branch-to-work-item-via-command-line) between commit and work item.

```bash
git commit -m "Example commit message #345"
```

## When to commit

## When to pull origin master

## Articles

- [How to write a git commit message](https://chris.beams.io/posts/git-commit/)
- [Atomic commits](https://www.freshconsulting.com/atomic-commits/)
- [Pro Git](https://git-scm.com/book/en/v2) free book
