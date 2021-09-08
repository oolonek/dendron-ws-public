---
id: kjCZnMBrXYokZny7loss4
title: Git
desc: ''
updated: 1630424707973
created: 1630424670253
stub: true
---


# Nice intro

Looks good for tuto and convince of git adoption Version Control with Git

https://carpentries-incubator.github.io/git-novice-branch-pr/
# Get info of the git remote

`git config --get remote.origin.url`

# Get history as a graph

```
git fetch
git log --all --decorate --oneline --graph
```


# Pull

https://stackoverflow.com/a/4924044

So I imagine you want to do something like:

`git pull origin dev`

To set it up so that it does this by default while you're on the dev branch:

`git branch --set-upstream-to dev origin/dev`


# Reset to specific commit and push to master 

 git reset --hard <commit-hash>
 git push -f origin main
 
