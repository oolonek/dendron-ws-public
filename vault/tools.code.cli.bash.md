---
id: cMOaRh3TUHfw6FtdribBg
title: Bash
desc: ''
updated: 1666263577575
created: 1610975606358
---

# Rename files

```bash
for f in *.png; do echo mv "$f" "${f/_*_/_}"; done
```

Remove echo 

https://stackoverflow.com/a/24103055

[[#tremendous|tag.tremendous]]

# List all files and folder in a graphical tree in terminal

You need to 
`brew install tree`

Then you can `tree` or `tree -lart`
# List all files and their full path

ls -d -1 "$PWD/"*.*


# bash upgrade on mac

https://itnext.io/upgrading-bash-on-macos-7138bd1066ba

Had some problem when running the build.sh script of manubot.
Because of this error 

build/build.sh: line 50: ${BUILD_PDF,,}: bad substitution
Turns out that ,, are not 

https://stackoverflow.com/a/47815884


# create a folder architecture

mkdir -p adria-leboeuf-group/{docs/MAPP_project_00014/MAPP_batch_00019/{metadata,results},src/MAPP_project_00014/MAPP_batch_00019/}


mkdir -p {metadata,results/{cytoscape,met_annot_enhancer,metaboanalyst,mzmine,stats,sirius,tmp}}

mkdir -p results/{cytoscape,met_annot_enhancer,metaboanalyst,mzmine,stats,sirius,tmp} && touch results/{cytoscape/.gitignore,met_annot_enhancer/.gitignore,metaboanalyst/.gitignore,mzmine/.gitignore,stats/.gitignore,sirius/.gitignore,tmp/.gitignore}

mkdir -p {metadata,results/{cytoscape,met_annot_enhancer,metaboanalyst,mzmine,stats,sirius,tmp}} && touch {metadata/.gitignore,results/{cytoscape/.gitignore,met_annot_enhancer/.gitignore,metaboanalyst/{.gitignore,placeholder.out},mzmine/{.gitignore,placeholder.out},stats/.gitignore,sirius/{.gitignore,placeholder.out},tmp/.gitignore}}