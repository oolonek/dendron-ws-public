---
id: 0HNwN2BVtZRCgGI1AE0uD
title: New_recipee
desc: ''
updated: 1638447615366
created: 1638447262832
---

# New recipee (draft) fro multivault setup

Thursday 02 December 2021 

Since some time the 11ty publishing system as changed and this implies some modification on the previous multivault procedure.
I will try to summarise the steps here while setting up a dendron fro a MAPP collaborator


Create private git 
Clone private git
ctrl shit p initilaize workspace
push to git

We then follow stuff here https://wiki.dendron.so/notes/e5st4LFLtIwwbQmC6JBaF/


npm install -g @dendronhq/dendron-cli


npm install -g yarn

echo .next >> .gitignore

dendron publish init


https://wiki.dendron.so/notes/FnK2ws6w1uaS1YzBUY3BR/


npm init -y 
npm install --save @dendronhq/dendron-cli

git checkout -b pages
git push -u origin HEAD


git checkout main

mkdir -p .github/workflows
ni .github/workflows/publish.yml


