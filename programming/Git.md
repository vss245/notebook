# Git basics

- version control allows to track changes in projects, review changes, combine code from multiple people 
- a repository is a collection of code
- content:
  - working directory -> staging -> local repo -> remote repo (master)
  - ![image](https://cdn-media-1.freecodecamp.org/images/1*iL2J8k4ygQlg3xriKGimbQ.png)

#### Configuring:

```shell
git config --global user.name "YOUR_USERNAME" 
git config --global user.email "YOUR_EMAIL" 
```

Git now requires a Personal Access Token, which can be created in settings and added in place of a password.

#### Commands:

- git clone (url) clones a repository to the local machine
- git add - adds to staging area
- git commit -m “comment” - adds a commit
- git push - pushes to local
- git fetch - from remote to local
- git merge - from local to working
- git pull - get updates from remote (fetch and merge remote changes)
- git diff - show differences that aren’t yet staged
- git remote add origin - adds an origin (e.g. remote repo)
- git tag 1.0.0 - tag releases

#### Collaborating:

- branches are used to develop features separately from the main code
  - git checkout -b feature_x - switch to branch feature_x
  - git checkout main - switch back to main
  - git branch -d feature_x - delete branch
  - git push origin feature_x - pushes a branch
  - git merge feature_x - to merge a branch into the active branch
- git fetch + git merge = git pull
- git log to study a repository

#### Fixing mistakes:

- git checkout -- file.py - replaces changes in working tree with current version from HEAD
- to remove all local changes and commits, do git fetch origin, then git reset --hard origin/main
  - this is bad and dangerous! 