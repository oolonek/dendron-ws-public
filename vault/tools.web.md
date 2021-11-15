---
id: ykyXmoqr752B7Eo1mKkBF
title: Web
desc: ''
updated: 1636730653639
created: 1611825283591
---

[TOC]


# Web hosting of a single page 
2021-01-28 10:29
## Context
I need to share html rendered md notes coming from dendrons private daily journal notes. I use these as an electronic lab notebook and sometime want to share them to collaborators instead of preparing a ppt or keynote slide presentation.
## Need
What I currently have is the daily journal notes as .md files. I can render them as .html using MPE. Make a TOC as a sidebar (just add [TOC] at the head of the file), display images, mermaid diagrams etc. They can be automatically published in the github pages. This is OK for dendron notes that I want to publish. However I need to find a solution to efficiently share private notes as html files.

The remote notes :

- [ ] should be accessible by a simple link, no download required
- [ ] should rendered the exact same way as the dendrons published notes
- [ ] should be versionable by git or similar
- [ ] should be automatically updated upon local changes
- [ ] should be self encapsulated (if i have them hosted on a git the user whith the link to note C should not be able to jump to upper levels or see note A)


## Task (of the note/paragraph/text/paper/project)

This is what I did up to now and what I plan to do to tackle this

- [x] ~~recreated this ctno snippet~~

- [x] ~~created this note~~

- [ ] check for hosting solutions

    - [x] ~~dropbox~~

    Not good anymore as the discontinued the direct disply of html files. Would have been a perfect solution.
    https://superuser.com/questions/764641/how-to-serve-html-off-my-dropbox

    - [x] ~~https://www.fast.io/~~ (appears to be discontinued as of 2021-01-16)
    - [ ] http://pomf.se/
    - [ ] https://www.netlify.com/
    - [ ] https://wowchemy.com/
        - [ ] https://www.jameswright.xyz/post/deploy-hugo-academic-using-githubio/

## Object (of the note/paragraph/text/paper/project)
This is a self contained ctno snippet. It does not aim to introduce anything other than itself.
That was the object. //TODO Snippets. Work on different and more adapted snippets (self sufficient, introductory etc ...)


## Hugo


https://www.ctomlinson.net/post/building-a-website-with-hugo-academic/

