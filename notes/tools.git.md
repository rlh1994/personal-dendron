---
id: DXEMdQlV1EAiXrToYyjOA
title: Git
desc: ''
updated: 1641815254830
created: 1641804280014
---


# Git
Git is a local-based version control system for tracking changes to (mostly) plain text files. It started life as a tool used within software but can be used for data analysis, note taking, and any file that has been written in plain text. 

The benefits of using git, or any version control system are
1. Tracking of changes to files, allowing to see and revert to historic versions of files
2. Using branches you can have multiple versions of a file available on the same machine without naming conflicts, and can switch between them very easily
3. Compared to storing multiple versions of the file (e.g. named with the timestamp) git only tracks _changes_ to your files, meaning it takes up far less space and reduces duplication.

Being a local-based program it is entirely possible to use git only on your machine, never interacting with any other machine or the internet, however you gain many more benefits from hosting your work on a web-based client such as [[tools.git.github]] or [[tools.git.gitlab]]. Combing local git with one of these (or other) tools means as well as above you can:
1. Sync work between machines without needing to manually transfer
2. Have nice GUI interfaces to complete things such as merge requests and conflicts
3. Gain additional functionality over a project e.g. issue tracking and discussions.

# Setup
Once first installed you need to run the following commands in the command line:
```bash
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```

# Key Terms
![[tools.git.terms#repository:#*]]
![[tools.git.terms#branch:#*]]

# Workflow
![](/assets/images/2022-01-10-09-58-54.png)

The usual flow when working with a remote repo is:
1. Clone the repo using `git clone` ![[tools.git.commands#clone:#*]] or use `git pull` if already cloned to check for any new commits ![[tools.git.commands#pull:#*]]
2. Optionally create a new branch and switch to it using `git branch` ![[tools.git.commands#branch:#*]]
3. Make changes to the files locally
4. Use `git add` to stage these changes ![[tools.git.commands#add:#*]]
5. Create a commit using `git commit` with a useful message ![[tools.git.commands#commit:#*]]
6. Go to step 2 and repeat until e.g. end of day
7. Use `git push` to push any commits made back to the remote ![[tools.git.commands#push:#*]]
8. If development has been completed and you were working on a branch, raise a merge request on the remote and switch branches back on your local machine. 
9. Repeat.
