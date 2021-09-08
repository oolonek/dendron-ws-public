---
id: 1zIrSWjXkUv4Lx4VeWLgj
title: Biblio
desc: ''
updated: 1611681995788
created: 1609570147699
---
# Bib integration in dendron

Messing around with pandoc citer and trying to integrate bibliography management in dendron

The markender extension (<https://github.com/mjwsteenbergen/markender>) is causing conflict with pandoc citer for the autocompletion.
Deactivate Markender

Conflict thrown  [[projects.tramadol]] 

Error: Command failed: pandoc --from=markdown-raw_tex+tex_math_single_backslash --to=html --katex --filter pandoc-citeproc
Error reading bibliography /Users/pma/Documents/library_formatted.bib (line 60541, column 1):
unexpected end of input
expecting "}", "\\" or "{"
Error running filter pandoc-citeproc:
Filter returned error status 1

Now trying to troubleshoot the file using bibdesk

## Bib file formatting

Bib file formatting is required to avoid the previous error. This error is somehow misleading because it indicates that the error comes from the end of the file ... and it's not the case, rather a curly brace somewhere which is not closed.

From the automatically sync .bib of Mendeley, make a copy and ctrl+F replace all { by \\'{ and all all } by \\'}
This should make the trick.

See [[cli.sed_bash]] for the recipee.

And here goes a Note reference 

((ref: [[cli.sed_bash]]))

//DONE check Amoeba splitting of notes (here is a typical application case ... Automatization and sed lines should go in separate notes as these can be used for other purposes than just the .bib reformating) 2021-01-02 17:30 checking .... and just splitted the above sed commands

//TODO understand the way to have the bibliography display on the published version of dendron. Not the case at the moment see [[projects.tramadol]]

//TODO set bibliography globally


