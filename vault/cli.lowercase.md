---
id: l1i6gksd9rbsljpkpa5c0s5
title: Lowercase
desc: ''
updated: 1647785912065
created: 1647785862905
---

https://stackoverflow.com/a/7787159/4908629


❗ Mind were you are doing this ! It's not possible to go back :P 


for f in *; do mv "$f" "$f.tmp"; mv "$f.tmp" "`echo $f | tr "[:upper:]" "[:lower:]"`"; done



