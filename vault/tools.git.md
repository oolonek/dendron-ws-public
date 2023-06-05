---
id: kjCZnMBrXYokZny7loss4
title: Git
desc: ''
updated: 1685640791711
created: 1630424670253
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
 

# What should you do when you get the infamous "You have divergent branches and need to specify how to reconcile them."

```
hint: You have divergent branches and need to specify how to reconcile them.
hint: You can do so by running one of the following commands sometime before
hint: your next pull:
hint: 
hint:   git config pull.rebase true   # rebase
hint:   git config pull.ff only       # fast-forward only
hint: 
hint: You can replace "git config" with "git config --global" to set a default
hint: preference for all repositories. You can also pass --rebase, --no-rebase,
hint: or --ff-only on the command line to override the configured default per
hint: invocation.
```

https://stackoverflow.com/a/62653400/4908629


## What is the git fast-forward option ?
https://blog.mergify.com/what-is-a-git-merge-fast-forward/

> When Git detects that your commit is about to be merged into your project's main branch without the main branch having been modified since your feature branch was first made, it chooses to use a fast-forward merge instead of a three-way merge. Fast-forward merges literally move your main branch's tip forward to the end of your feature branch. This keeps all commits created in your feature branch sequential while integrating it neatly back into your main branch.
> 
> 

## For git sensitive information removal

https://rtyley.github.io/bfg-repo-cleaner/

