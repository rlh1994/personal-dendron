---
id: jRvyqJZs8ZxK9PTg2eUoI
title: Terms
desc: ''
updated: 1641832405401
created: 1641805079644
---


#### Repository
A repository (repo) is the largest unit in the git system, it comprises an entire folder on your machine and all tracked work within that folder. Note you that can locally have files in a folder that are not tracked by git and these would not be part of your repository. The repo also includes the git history itself and all [[branches|tools.git.terms#branch]] that are created. 

#### Tracked
Tracked files simply means that they are seen by and available to version control via git. By default all files are tracked until they are excluded via your `.gitignore` file.

#### Local
Local means on your machine, if you have a local repo it is stored and tracking on your machine. If you have a local copy of a repo, it is on your machine.

#### Remote
Remote could either refer to the command itself, or the concept of a remote repo. A remote repo is a repo that is stored somewhere other than your machine, usually one of [[tools.git.github]] or [[tools.git.gitlab]]. To interact with the remote you would [[push|tools.git.commands#push]] and [[pull|tools.git.commands#pull]] your commits to the remote and from it respectively.

#### Branch
A branch in your repo is a parallel version of your (tracked) files that you can make changes and commits to, but those commits only exist on that branch. This means you can switch branches at any time and have different versions of your files (but with the same file name) on your machine. Traditionally you would have a development branch where fixes/new features would be first written, then a test branch where your tester/QA would evaluate the product to ensure it all works as expected, then your master/main branch is the one that your product actually builds off. You may have a branch for each development/bug fix, you may make branches for many other reasons - but the benefit of them remains the same. 

You can create a branch using the [[branch|tools.git.commands#branch]] command, and you may at times need to re-align other files with your main branch, which can be done using the [[rebase|tools.git.commands#rebase]] command.

#### Merge
When you have a change in some branch (let's call it `dev`) that you want to implement into some other branch (call it `main`) you need to merge from `dev` to `main`. While it is possible to do this using the [[merge|tools.git.commands#merge]] command, it is often easier to do this using a web interface such as those available in [[tools.git.github]] or [[tools.git.gitlab]]. These tools offer nice overviews of all changes, highlights **merge conflicts** (where the file has been changed on both branches and you must decide which changed version to keep), and allows for things such as code review to take place much easier. If it is a simple merge, the command line is fine but for anything else use a GUI - especially if you are working as part of a team. 

When you do this merge you have the option to keep the `dev` branch or delete it (note it will only delete it where the merge was completed, so if you do the merge on GitHub then you will still have the branch locally), and the option to _squash_ the commits (so it looks like there was a single commit with all your changes to the `main` branch). What you choose for each of these depends on the use case and your ways of working. 

#### gitignore
The `.gitignore` file in any repo is a list of files or filetypes that should be ignored by git when tracking changes. Most languages have a default `.gitignore` file that you can find [online](https://www.toptal.com/developers/gitignore) to avoid tracking files that aren't relevant/are binary type files. Most git clients will allow you to add files or all `*.type` files to the gitignore in the GUI. 

**NOTE:** adding a file to the `.gitignore` _after_ already commiting it does not remove it from the history - if you accidentaly commit a secret file you will need to remove the entire commit, if you want to remove it even further back you will may need to just restart your repo.
