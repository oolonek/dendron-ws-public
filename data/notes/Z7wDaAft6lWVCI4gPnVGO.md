
(sublime ZK imported)

# idea_datawarrior
tags = #database #datawarrior #bibliography o

Add bibliographic reference to each compounds using the google scholar patents links functionality of DataWarrior.

It looks like an automatic query of the SMILES string can be done.
Example 

https://patents.google.com/?q=SMILES%3dO%3dC1(OC2(C(C4(CCCCN3(C4(C(C2(C1C))CC3))))CC))&patents=false&scholar&oq=SMILES%3dO%3dC1(OC2(C(C4(CCCCN3(C4(C(C2(C1C))CC3))))CC))

# directly fetches results and download them as csv file
https://patents.google.com/xhr/query?url=q%3DSMILES%253dO%253dC1(OC2(C(C4(CCCCN3(C4(C(C2(C1C))CC3))))CC))%26patents%3Dfalse%26scholar%26oq%3DSMILES%253dO%253dC1(OC2(C(C4(CCCCN3(C4(C(C2(C1C))CC3))))CC))&exp=&download=concepts


# actually it goes even further as on can add terms to filter the query.
Here for example terms form the European Patent Office corresponding to Medicinal preparations of undetermined constitution containing material from algae, lichens, fungi or plants, or derivatives thereof, e.g. traditional herbal medicines (A61K36/00) https://worldwide.espacenet.com/classification#!/CPC=A61K36/00

https://patents.google.com/xhr/query?url=q%3DSMILES%253dO(C3(%253dC1(C(NC2(%253dC1C%253dCC%253dC2O))%253dC(C%253dC)N%253dC3)))C%26q%3DA61K%26patents%3Dfalse%26scholar%26sort%3Dold&exp=&download=concepts

Note that the %3D character can pe passed to = for more readibility

<https://patents.google.com/xhr/query?url=q=SMILES%253dO(C3(%253dC1(C(NC2(%253dC1C%253dCC%253dC2O))%253dC(C%253dC)N%253dC3)))C%26q=A61K36/00%26patents=false%26scholar%26sort=old&exp=&download=concepts>


Note that a scrapper as been written to download all associated pdfs

https://github.com/wenyalintw/Google-Patents-Scraper

https://patents.google.com/xhr/query?url=q=SMILES%253dO(C3(%253dC1(C(NC2(%253dC1C%253dCC%253dC2O))%253dC(C%253dC)N%253dC3)))C%26q=A61K36/00%26patents=false%26scholar%26sort=old
