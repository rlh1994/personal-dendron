---
id: mNWDextJfhiYIU9qZkubF
title: Commands
desc: ''
updated: 1641830837864
created: 1641806379582
---


#### add
```bash
git add <files>
```
`git add` is used to add files that have changes to convert them to staged changes (ready for the next commit). The most common usage is usually `git add *` which will add all tracked files with changes to the next commit. 

https://git-scm.com/docs/git-add

#### commit
```bash
git commit -m 'commit message here'
```
`git commit` takes all staged files added via `git add` and creates a commit snapshot of these files at this time. It is good practise to provide a short message using the `-m` argument to provide context to the changes in this commit e.g. 'fixed scrolling bug'.

https://git-scm.com/docs/git-commit
#### push
```bash
git push
```
`git push` sends any local commits to the remote (assuming it has been set up as default in advance).

https://git-scm.com/docs/git-push

#### pull
```bash
git pull
```
`git pull` gets any remote commits and copies them to the local repo.

https://git-scm.com/docs/git-pull

#### branch
```bash
git branch <branch_name>
git checkout <branch_name>
git branch -m <old_name> <new_name>
git branch -d <branch_name>
```
`git branch` will print out the name of all branches that exist locally, and a * will display the current working branch. `git branch new_branch` will create a new branch with that name, but you must then call `git checkout new_branch` to switch to that branch (or call `git checkout -b new_branch` to do it all in one go). Rename a branch using `git branch -m old_name new_name`. Finally to delete a branch you can use `git branch -d new_branch`.

https://git-scm.com/docs/git-branch

#### rebase
```bash
git rebase <base>
```
`git rebase` will take commits on your current branch, but bring in any new commits on the base branch as well. This can be used to keep a development branch up-to-date with the main branch.  

https://git-scm.com/docs/git-rebase

#### merge
```bash
git merge <branch>
```
`git merge` will take a branch and merge it into the current branch. It is better to do this via a GUI or web-service rather than command line due to complexities and conflicts. 

https://git-scm.com/docs/git-merge

#### status
```bash
git status
```
When run within a repo this command will show the status of the repo (on the current branch) including staged files, untracked files (created since last commit), and changed tracked files that are not yet staged. It will also tell you if you are behind/ahead of the remote if applicable.

https://git-scm.com/docs/git-stat

#### clone
```bash
git clone <url>
```
`git clone` will clone a repostiory from a remote to a local folder (it will create a folder with the name of the repo in your current directory where the command is run). It will clone all files, history, and branches. It will also set the remote for `push` by default so it is often easier to create a repo on a remote than clone rather than create local then setup the remote and push. The url can take a few forms, but usually ends in a `.git`.

https://git-scm.com/docs/git-clone
