---
id: qcUnyE9eaS2PVPPngKeB1
title: Sparql
desc: ''
updated: 1663010700763
created: 1611593110381
---

# SPARQL queries



# all compounds produced by a given taxon or group of taxa (including children taxa) : 

https://w.wiki/4CMd

with ref

https://w.wiki/4CMg



# all compounds produced by a given taxon or group of taxa (including children taxa) which have a described bioactivity : 

https://w.wiki/3YMo

resumed as treemap https://w.wiki/3YMt

for archive on zenodo https://w.wiki/4N8G
results https://w.wiki/4N8J



## All organisms containing compound for which a given MeSh id has been reported.

Change MeSH Id according to https://meshb.nlm.nih.gov/search

https://w.wiki/vo9

### displayed as a treemap

https://w.wiki/zkK


## compounds in organisms who have a parent taxon with a given taxon name

https://w.wiki/vo$

## compounds in organisms who have a parent taxon with a given taxon name - grouped and counted 

https://w.wiki/368M

## compounds in organisms who have a parent taxon with a given taxon name - with mf and accurate mass


https://w.wiki/36Ki



## compounds displaying a found in a taxon property

https://w.wiki/q$H

## idsm powered !!!


https://w.wiki/xMJ

[[mail_jakub|scratch.2021.02.02.150258.mail_jakub]] 

## genus counting indole substrutcures

This SPAQRL query is based on a proposition of Jakub Galgonek <jakub.galgonek@uochb.cas.cz> (https://idsm.elixir-czech.cz/) and adapted by Pierre-Marie Allard (pierre-marie.allard@unige.ch)
It returns an order list of organisms known to produce chemical compounds having an indolic moiety.
The organisms are aggregated at the parent taxon level, and the list is ordered by number of compound occurence in the parent t

https://w.wiki/xMN


## all molecules isolated by author X

https://w.wiki/32D6
https://w.wiki/32$m


## count of the authors having isolated a given scaffold

https://w.wiki/32DF

## compare authors by count of compound

https://w.wiki/32Vb
https://w.wiki/32Vk (bar-chart)


## compare authors by count of compound (substructure-refinable)

https://w.wiki/32Vd

## compare authors by count of compound (structuresimilarity-refinable)

https://w.wiki/32Vg (indolic)
https://w.wiki/32Vj (bubblechart - indolic)
https://w.wiki/32Vi (bubblechart - tropanic)

## count of authors isolating substances with a given role

https://w.wiki/32Vr

## all distinct article/substances/org for a given biological role

https://w.wiki/32Vu

## all disticnt antibiotics

https://w.wiki/32Vv


## drug-prot interaction 

```SPARQL
SELECT DISTINCT ?parent_taxon ?parent_taxon_name ?compound ?interaction ?compoundLabel ?geneLabel ?biological_processLabel ?diseaseLabel WHERE {
  #?compound wdt:P2868 ?mesh.
  #?mesh wdt:P486 "D000962".
  ?compound wdt:P235 ?inchikey.
  {
    ?compound p:P703 ?statement.
    ?statement ps:P703 ?taxon.
    ?taxon wdt:P171 ?parent_taxon.
    OPTIONAL { ?taxon wdt:P171 ?parent_taxon. }
    OPTIONAL { ?parent_taxon wdt:P225 ?parent_taxon_name. }
    {
      ?statement prov:wasDerivedFrom ?ref.
      ?ref pr:P248 ?reference.
      ?reference wdt:P356 ?reference_doi;
        wdt:P1476 ?reference_title.
    }
   #?compound p:P129 ?interaction.
   #?interaction wdt: wd:Q21119831.
    
    ?compound wdt:P129 ?gene_product .   # drug interacts with a gene_product
    ?gene wdt:P688 ?gene_product .  # gene_product (usually a protein) is a product of a gene (a region of DNA)
    ?disease  wdt:P2293 ?gene .    # genetic association between disease and gene
    ?disease wdt:P279*  wd:Q12078 .  # limit to cancers wd:Q12078 (the * operator runs up a transitive relation..)
    ?gene_product wdt:P682 ?biological_process . #add information about the GO biological processes that the gene is related to 

    ?biological_process (wdt:P361|wdt:P279)* wd:Q14599311.
  }
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}
  
GROUP BY ?parent_taxon ?parent_taxon_name ?compound ?interaction ?compoundLabel ?geneLabel ?biological_processLabel ?diseaseLabel
#ORDER BY DESC (?count)
```


## Generic LOTUS queries

https://w.wiki/$Q$
https://w.wiki/$R3
https://w.wiki/$RD apparently working !
https://w.wiki/$RR with wd: for structure and org
https://w.wiki/$RU wd: for everyone ...still ok
https://w.wiki/$SF full monty

## Sachem non-permanent endpoint

https://idsm.elixir-czech.cz:2443/sachem/#/search


## Sachem grand parents
https://w.wiki/32Wz

## Retrun compound present in invasive species

https://w.wiki/32fa
https://w.wiki/32fc

## check taxon for a givin INChikey (regex)

https://w.wiki/32j3

## chemotax graph queries

https://w.wiki/32q9
https://w.wiki/32qC


https://w.wiki/32qN


# to tweet 

All the compounds found in the Streptomyces avermitilis taxon and the references documenting this link. 
https://w.wiki/33V$

We can remove the references to get all unique compounds found in the Streptomyces coelicolor

https://w.wiki/33WG



All the biological taxa where the chemical compound erysodine is found in.
https://w.wiki/33WA



# molecules found within vegetables

https://w.wiki/4EAh

# molecules found within toxic plants


https://w.wiki/4EAw

#  mlecules in IUCN threatned species

https://w.wiki/4EGg

https://w.wiki/4EHQ



# looking for molecules present in old species according to life span

https://w.wiki/4EH8
https://w.wiki/4EHB

with preclass

https://w.wiki/4EHD

and prepreclass 

at all levels
https://w.wiki/4EHH

at a single level

https://w.wiki/4EHJ


classed by chem classes
https://w.wiki/4EHP




# Messing around with pathways

https://w.wiki/4EK7

original query 

https://w.wiki/4EK9


# highest mountains in Switzerland 

https://w.wiki/4EKE


# all biologist with a twitter account


https://w.wiki/4EKW

strictly biologists
https://w.wiki/4EKM

educated in Switzerland 

https://w.wiki/4EKk

# example for prsenattion UniFr

https://w.wiki/4EMf 
All compounds + ref for S. coelicolor

https://w.wiki/4EMo (bioact listed)

#  Compounds from species wuth given IUCN status and lifespan
https://w.wiki/4EMw

# compounds in taxa and children filtered by SMILES pattern regex

https://w.wiki/4JWv

# Melochia genus query

https://w.wiki/4VYy


# IDSM queries 

PREFIX sachem: <http://bioinfo.uochb.cas.cz/rdf/v1.0/sachem#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX bd: <http://www.bigdata.com/rdf#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wdtn: <http://www.wikidata.org/prop/direct-normalized/>
PREFIX p: <http://www.wikidata.org/prop/>
PREFIX prov: <http://www.w3.org/ns/prov#>
PREFIX ps: <http://www.wikidata.org/prop/statement/>
PREFIX pr: <http://www.wikidata.org/prop/reference/>
PREFIX endpoint: <https://idsm.elixir-czech.cz/sparql/endpoint/>



#title: Which are the available referenced structure-organism pairs on Wikidata? (example limited to 1000 results)
SELECT DISTINCT ?structure ?structure_inchikey ?taxon ?taxon_name ?reference ?reference_doi WHERE {
  ?structure wdt:P235 ?structure_inchikey;       # get the inchikey
    p:P703[                                      # statement found in taxon
     ps:P703 ?taxon;                             # get the taxon
     (prov:wasDerivedFrom/pr:P248) ?reference ]. # get the reference
  ?taxon wdt:P225 ?taxon_name.                   # get the taxon scientific name
  ?reference wdt:P356 ?reference_doi.            # get the reference DOI
}
LIMIT 10




PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX sachem: <http://bioinfo.uochb.cas.cz/rdf/v1.0/sachem#>
PREFIX endpoint: <https://idsm.elixir-czech.cz/sparql/endpoint/>

SELECT * WHERE {
  SERVICE endpoint:chebi {
    ?COMPOUND sachem:substructureSearch
        [ sachem:query "CC(=O)Oc1ccccc1C(O)=O" ]
  }
  ?COMPOUND rdfs:label ?o
}




# title: Compounds of the Melochia genus bearing the quinoline substructure

https://w.wiki/4wbY


# all articles documenting found in taxonn Prop by authors of a given country 

https://w.wiki/4z7M



-----


PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX jlw: <https://www.sinergiawolfender.org/jlw/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX p: <http://www.wikidata.org/prop/>
PREFIX ps: <http://www.wikidata.org/prop/statement/>
PREFIX prov: <http://www.w3.org/ns/prov#>
PREFIX pr: <http://www.wikidata.org/prop/reference/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>
PREFIX wdraw: <http://www.wikidata.org/>
PREFIX vit: <https://www.sinergiawolfender.org/vit/>

SELECT ?chemical_compound ?compoundLabel ?queried_taxa  ?queried_taxaLabel ?queried_taxall ?queried_taxallLabel ?pfcode WHERE {
       
SERVICE <https://query.wikidata.org/sparql> {
  VALUES ?queried_taxa {
    wd:Q310915
  }
  {
    ?chemical_compound p:P703 ?stmt.# We selecte chemical classes having the found in taxon statement
    ?queried_taxall wdt:P171* ?queried_taxa.
    ?stmt ps:P703 ?queried_taxall. # and the restrict the found in taxon statement to match our queried taxa
  }
 ?chemical_compound rdfs:label ?compoundLabel.
 ?queried_taxa rdfs:label ?queried_taxaLabel.
 ?queried_taxall rdfs:label ?queried_taxallLabel.
        
 FILTER (LANG(?compoundLabel) = "en") . # filter for English
 FILTER (LANG(?queried_taxaLabel) = "en") .
 FILTER (LANG(?queried_taxallLabel) = "en") .
}
    
?pfcode       jlw:is_from_plant_part               ?plant_part;
              vit:has_taxon ?taxon.
    
?taxon jlw:has_wd_QID ?queried_taxall. 
    
}







PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX jlw: <https://www.sinergiawolfender.org/jlw/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX p: <http://www.wikidata.org/prop/>
PREFIX ps: <http://www.wikidata.org/prop/statement/>
PREFIX prov: <http://www.w3.org/ns/prov#>
PREFIX pr: <http://www.wikidata.org/prop/reference/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>
PREFIX wdraw: <http://www.wikidata.org/>
PREFIX vit: <https://www.sinergiawolfender.org/vit/>

SELECT ?chemical_compound ?mf ?mf_formatted ?compoundLabel ?queried_taxa  ?queried_taxaLabel ?queried_taxall ?queried_taxallLabel ?pfcode ?labprocess ?feature ?sirius_formula ?sirius_formula_string WHERE {
       
SERVICE <https://query.wikidata.org/sparql> {
  VALUES ?queried_taxa {
    wd:Q310915
  }
  {
    ?chemical_compound p:P703 ?stmt.# We selecte chemical classes having the found in taxon statement
  OPTIONAL { ?chemical_compound wdt:P231 ?cas. }
  OPTIONAL { ?chemical_compound wdt:P233 ?smiles_canonical. }
  OPTIONAL { ?chemical_compound wdt:P234 ?inchi. }
  OPTIONAL { ?chemical_compound wdt:P592 ?chembl. }
  OPTIONAL { ?chemical_compound wdt:P662 ?pubchem. }
  OPTIONAL { ?chemical_compound wdt:P683 ?chebi. }
  OPTIONAL { ?chemical_compound wdt:P2017 ?smiles_isomeric. }
  OPTIONAL { ?chemical_compound wdt:P274 ?mf. }
  OPTIONAL { ?chemical_compound wdt:P2067 ?mass. }
            #BIND(LCASE(STR(?mf)) as ?lowmf)
            #BIND(REPLACE(STR(?mf),"₀₁₂₃₄₅₆₇₈₉","B") AS ?mf_b) .
            BIND(REPLACE(REPLACE(REPLACE(REPLACE(REPLACE(REPLACE(REPLACE(REPLACE(REPLACE(REPLACE(STR(?mf),"₀","0"),"₁","1"),"₂","2"),"₃","3"),"₄","4"),"₅","5"),"₆","6"),"₇","7"),"₈","8"),"₉","9") AS ?mf_formatted) .


            
    ?queried_taxall wdt:P171* ?queried_taxa.
    ?stmt ps:P703 ?queried_taxall. # and the restrict the found in taxon statement to match our queried taxa
  }
 ?chemical_compound rdfs:label ?compoundLabel.
 ?queried_taxa rdfs:label ?queried_taxaLabel.
 ?queried_taxall rdfs:label ?queried_taxallLabel.
        
 FILTER (LANG(?compoundLabel) = "en") . # filter for English
 FILTER (LANG(?queried_taxaLabel) = "en") .
 FILTER (LANG(?queried_taxallLabel) = "en") .
}
    
?pfcode       jlw:is_from_plant_part               ?plant_part;
              jlw:has_lab_process ?labprocess;
              vit:has_taxon ?taxon.
?labprocess jlw:has_MZmine_chromatogram ?mzmine_chromatogram .
    
?mzmine_chromatogram jlw:has_MZmine_feature ?feature .

?feature jlw:has_SIRIUS_formula ?sirius_formula.
    
?sirius_formula jlw:has_SIRIUS_formula_string ?sirius_formula_string.
    
?taxon jlw:has_wd_QID ?queried_taxall. 
    
FILTER(?mf_formatted = ?sirius_formula_string)
}

# Compounds produced by plants endemic to New caledonia

https://w.wiki/57ap

cleaner with mass and mf

https://w.wiki/57hN


# listing compounds in meals

https://w.wiki/5Bs7


https://w.wiki/5Bs9

# Compounds of the Arachnida class

https://w.wiki/5Doy


# Compounds from taxa and children clean

https://w.wiki/5LJf


# References and occurences of Alstonine 

https://w.wiki/5WXP

# compare occurences in WD of entries with a given taxon id  (OTL versus WFO)

https://w.wiki/5WYx



## endpoints

https://www.wikidata.org/wiki/Wikidata:Lists/SPARQL_endpoints



#### quest query mod from Mietchen to compounds (not working)

# Pay attention to edge cases
SELECT DISTINCT ?n_formatted
(CONCAT(
REPLACE(STR(?i), ".*Q", "Q"), "|P921|", REPLACE(STR(?ta), ".*Q", "Q"), "|P1932|", (CONCAT("\"", ?a, "\"")), "|S887|Q69652283") AS ?QuickStatements)
WITH {
SELECT DISTINCT ?ta WHERE {
SERVICE bd:sample { ?ta wdt:P31 wd:Q11173 . bd:serviceParam bd:sample.limit 5 }
}
LIMIT 2
}
AS %t
WITH
{ SELECT ?i ?n ?ta ?ti WHERE {
INCLUDE %t
        
?ta rdfs:label ?n.
FILTER (LANG(?n) = "en") .
BIND(REPLACE(STR(?n),"@en","") AS ?n_formatted) .
                                         

SERVICE wikibase:mwapi
{
bd:serviceParam wikibase:endpoint "www.wikidata.org";
wikibase:api "Generator";
mwapi:generator "search";
mwapi:gsrsearch ?n_formatted ;
mwapi:gsrlimit "max".
?i wikibase:apiOutputItem mwapi:title.
}
?i wdt:P1476 ?ti .
#MINUS {?i wdt:P921 ?ta }
#MINUS {?i wdt:P921 [wdt:P171* ?ta ] } 
FILTER (REGEX(LCASE(?ti), LCASE(CONCAT( "\\", "b", ?n_formatted ,"\\", "b"))))
FILTER (!REGEX(LCASE(?ti), LCASE(CONCAT( ?n_formatted ,"-"))))
FILTER (!REGEX(LCASE(?ti), LCASE(CONCAT( ?n_formatted ,"(.)virus"))))
FILTER (!REGEX(LCASE(?ti), LCASE(CONCAT( "pseudo(.?)", ?n_formatted))))
}
}
AS %i
WHERE {
INCLUDE %i
INCLUDE %t
BIND (SUBSTR(?ti, STRLEN(STRBEFORE(REPLACE(?ti, ?n, "=HELP=", "i"), "=HELP=")) +1, STRLEN(?n_formatted)) AS ?a)
}       


-----
No error but no results neither 

SELECT DISTINCT ?n_formatted
(CONCAT(
REPLACE(STR(?i), ".*Q", "Q"), "|P921|", REPLACE(STR(?ta), ".*Q", "Q"), "|P1932|", (CONCAT("\"", ?a, "\"")), "|S887|Q69652283") AS ?QuickStatements)
WITH {
SELECT DISTINCT ?ta ?n_formatted WHERE {
SERVICE bd:sample { ?ta wdt:P31 wd:Q11173 . bd:serviceParam bd:sample.limit 5000 }

?ta rdfs:label ?n.
FILTER (LANG(?n) = "en") .
BIND(REPLACE(STR(?n),"@en","") AS ?n_formatted) .
     

}
LIMIT 100
}
AS %t
WITH
{ SELECT ?i ?n_formatted ?ta ?ti WHERE {
INCLUDE %t
        
                                    

SERVICE wikibase:mwapi
{
bd:serviceParam wikibase:endpoint "www.wikidata.org";
wikibase:api "Generator";
mwapi:generator "search";
mwapi:gsrsearch ?n_formatted ;
mwapi:gsrlimit "max".
?i wikibase:apiOutputItem mwapi:title.
}
?i wdt:P1476 ?ti .
#MINUS {?i wdt:P921 ?ta }
#MINUS {?i wdt:P921 [wdt:P171* ?ta ] } 
FILTER (REGEX(LCASE(?ti), LCASE(CONCAT( "\\", "b", ?n_formatted ,"\\", "b"))))
FILTER (!REGEX(LCASE(?ti), LCASE(CONCAT( ?n_formatted ,"-"))))
FILTER (!REGEX(LCASE(?ti), LCASE(CONCAT( ?n_formatted ,"(.)virus"))))
FILTER (!REGEX(LCASE(?ti), LCASE(CONCAT( "pseudo(.?)", ?n))))
}
}
AS %i
WHERE {
INCLUDE %i
INCLUDE %t
BIND (SUBSTR(?ti, STRLEN(STRBEFORE(REPLACE(?ti, ?n_formatted, "=HELP=", "i"), "=HELP=")) +1, STRLEN(?n_formatted)) AS ?a)
}



-----

Works !!!

# adapted from Daniel Mietchen https://w.wiki/5a7K
SELECT DISTINCT ?n_formatted
(CONCAT(
REPLACE(STR(?i), ".*Q", "Q"), "|P921|", REPLACE(STR(?ta), ".*Q", "Q"), "|P1932|", (CONCAT("\"", ?a, "\"")), "|S887|Q69652283") AS ?QuickStatements)
WITH {
SELECT DISTINCT ?ta ?n_formatted WHERE {
SERVICE bd:sample { ?ta wdt:P31 wd:Q11173 . bd:serviceParam bd:sample.limit 5000 }
?ta p:P703 ?stmt.
?stmt ps:P703 ?taxa.
?ta rdfs:label ?n.
FILTER (LANG(?n) = "en") .
BIND(REPLACE(STR(?n),"@en","") AS ?n_formatted) .
}
LIMIT 25
}
AS %t
WITH
{ SELECT ?i ?n_formatted ?ta ?ti WHERE {
INCLUDE %t
SERVICE wikibase:mwapi
{
bd:serviceParam wikibase:endpoint "www.wikidata.org";
wikibase:api "Generator";
mwapi:generator "search";
mwapi:gsrsearch ?n_formatted ;
mwapi:gsrlimit "max".
?i wikibase:apiOutputItem mwapi:title.
}
?i wdt:P1476 ?ti .
MINUS {?i wdt:P921 ?ta }
#MINUS {?i wdt:P921 [wdt:P171* ?ta ] } 
#FILTER (REGEX(LCASE(?ti), LCASE(CONCAT( "\\", "b", ?n_formatted ,"\\", "b"))))
#FILTER (!REGEX(LCASE(?ti), LCASE(CONCAT( ?n_formatted ,"-"))))
#FILTER (!REGEX(LCASE(?ti), LCASE(CONCAT( ?n_formatted ,"(.)virus"))))
#FILTER (!REGEX(LCASE(?ti), LCASE(CONCAT( "pseudo(.?)", ?n))))
}
}
AS %i
WHERE {
INCLUDE %i
INCLUDE %t
BIND (SUBSTR(?ti, STRLEN(STRBEFORE(REPLACE(?ti, ?n_formatted, "=HELP=", "i"), "=HELP=")) +1, STRLEN(?n_formatted)) AS ?a)
}


https://w.wiki/5a8b

escaping dangling meta chracters https://w.wiki/5a8g

----- 

with taxa and compound

# Adapted from Daniel Mietchen https://w.wiki/5a7K
SELECT DISTINCT
(CONCAT(
REPLACE(STR(?i), ".*Q", "Q"), "|P921|", REPLACE(STR(?ta), ".*Q", "Q"), "|P1932|", (CONCAT("\"", ?a, "\"")), "|S887|Q69652283") AS ?QuickStatements)
WITH {
SELECT DISTINCT ?ta ?n_formatted WHERE {
SERVICE bd:sample { ?ta wdt:P31 wd:Q11173 . bd:serviceParam bd:sample.limit 5000 }
?ta p:P703 ?stmt.
?stmt ps:P703 ?taxa.
?ta rdfs:label ?n.
FILTER (LANG(?n) = "en") .
BIND(REPLACE(REPLACE(REPLACE(STR(?n),"@en",""),"\\+",""),"\\-","") AS ?n_formatted) .
}
LIMIT 25
}
AS %t
WITH
{ SELECT ?i ?n_formatted ?ta ?ti WHERE {
INCLUDE %t
SERVICE wikibase:mwapi
{
bd:serviceParam wikibase:endpoint "www.wikidata.org";
wikibase:api "Generator";
mwapi:generator "search";
mwapi:gsrsearch ?n_formatted;
mwapi:gsrlimit "max".
?i wikibase:apiOutputItem mwapi:title.
}
?i wdt:P1476 ?ti .
MINUS {?i wdt:P921 ?ta }
}
}
AS %i
WITH
{ SELECT ?j ?taxa ?ta ?ti WHERE {
INCLUDE %t
SERVICE wikibase:mwapi
{
bd:serviceParam wikibase:endpoint "www.wikidata.org";
wikibase:api "Generator";
mwapi:generator "search";
mwapi:gsrsearch ?taxa;
mwapi:gsrlimit "max".
?j wikibase:apiOutputItem mwapi:title.
}
?j wdt:P1476 ?ti .
MINUS {?j wdt:P921 ?taxa }
}
}
AS %j
WHERE {
INCLUDE %i
INCLUDE %j
INCLUDE %t
BIND (SUBSTR(?ti, STRLEN(STRBEFORE(REPLACE(?ti, ?n_formatted, "=HELP=", "i"), "=HELP=")) +1, STRLEN(?n_formatted)) AS ?a)
}


Using filter EXISTS 

https://w.wiki/5a8t

https://w.wiki/5a9B


------
Curating query 

# Adapted from Daniel Mietchen https://w.wiki/5a7K
SELECT DISTINCT ?taxa ?taxaLabel ?taxa_chem ?taxa_chemLabel ?ta ?taLabel ?ti 
(CONCAT(
REPLACE(STR(?ta), ".*Q", "Q"), "|P703|", REPLACE(STR(?taxa), ".*Q", "Q"), "|S248|", REPLACE(STR(?i), ".*Q", "Q")) AS ?QuickStatements)
WITH {
SELECT DISTINCT ?ta ?n_formatted ?taxa_chem WHERE {
SERVICE bd:sample { ?ta wdt:P31 wd:Q11173 . bd:serviceParam bd:sample.limit 25000 }
OPTIONAL { ?ta p:P703 ?stmt. }
OPTIONAL { ?stmt ps:P703 ?taxa_chem. }
?ta rdfs:label ?n.
FILTER (LANG(?n) = "en") .
BIND(REPLACE(REPLACE(REPLACE(STR(?n),"@en",""),"\\+",""),"\\-","") AS ?n_formatted) .
}
LIMIT 30
}
AS %t
WITH
{ SELECT ?i ?n_formatted ?ta ?ti ?taxa WHERE {
INCLUDE %t
SERVICE wikibase:mwapi
{
bd:serviceParam wikibase:endpoint "www.wikidata.org";
wikibase:api "Generator";
mwapi:generator "search";
mwapi:gsrsearch ?n_formatted ;
mwapi:gsrlimit "max".
?i wikibase:apiOutputItem mwapi:title.
}
?i wdt:P1476 ?ti .
?i wdt:P921 ?taxa.
?taxa wdt:P105 wd:Q7432.
FILTER (?taxa != ?taxa_chem)
}
}
AS %i
WHERE {
INCLUDE %i
INCLUDE %t
BIND (SUBSTR(?ti, STRLEN(STRBEFORE(REPLACE(?ti, ?n_formatted, "=HELP=", "i"), "=HELP=")) +1, STRLEN(?n_formatted)) AS ?a)
SERVICE wikibase:label { bd:serviceParam wikibase:language "en". }
}


https://w.wiki/5a9T

https://w.wiki/5a9g


# Solanum genus compounds

https://w.wiki/5h8g

# Solanum and erythroxylum genus compounds

https://w.wiki/5h9f

# Solanum and erythroxylum and Apocynaceae genus compounds

https://w.wiki/5h9p