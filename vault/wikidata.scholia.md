---
id: wl9UhkLI0rTQARpfVs77S
title: Scholia
desc: ''
updated: 1614787188353
created: 1614560154058
---

# Scholia

https://github.com/fnielsen/scholia

Scholia is a python package and webapp for interaction with scholarly information in Wikidata.

https://scholia.toolforge.org/

## Interest of Scholia as a curation page for LOTUS data

Can deal with chemical object 

https://scholia.toolforge.org/inchikey/QOVGHDRCAGYGEB-FFZYJECLSA-N


## Contribution 

https://github.com/fnielsen/scholia/blob/master/CONTRIBUTING.rst



## Egon's footnote 

Have you heard about Wikidata already? "Use Scholia and Wikidata to find scientific literature" is a new tutorial from my colleague Lauren Dupuis. https://laurendupuis.github.io/Scholia_tutorial/

## Daniels mail

Regarding the use of Scholia for visualizing structure-taxon relationships, I think this is very possible - we already have aspects for chemicals and for taxa, e.g. as per
https://scholia.toolforge.org/taxon/Q157892
or
https://scholia.toolforge.org/chemical/Q121802 .

With regards to forks, the most prominent example is probably
https://ordia.toolforge.org/ ,
which visualizes linguistic information based on the lexeme namespace in Wikidata.

Another thing to think about would be genome browsers like
http://wikigenomes.org/
or
https://chlambase.org/ .


adding additional SPARQL queries to existing Scholia pages is relatively straightforward (the main issue here is performance), so things like adding "found in taxon"-based queries to Scholia pages about compounds or taxa and perhaps also pathways could be solved quickly.

What might be even more interesting - but would require a bit more work - would be what we call subaspects, i.e. pages that combine two main classes, like https://scholia.toolforge.org/location/Q1748/topic/Q2539 .

With that in mind, we could think of things like
https://scholia.toolforge.org/compound/QID1/taxon/QID2
or
https://scholia.toolforge.org/taxon/QID3/compound/QID4 .

The work on such subaspects has been described in
https://www.wikidata.org/wiki/Q50813856 for the example of geodata,
which would probably be a good starting point when considering the effort involved.



## Other links

https://cthoyt.com/2021/01/23/updating-the-wikidata-integrator.html

A protocol for adding knowledge to Wikidata, a case report.
https://www.biorxiv.org/content/10.1101/2020.04.05.026336v2.full.pdf

