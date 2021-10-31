---
id: 6qK8k4MF0vooncgMJZw5W
title: Isfrag
desc: ''
updated: 1635171184446
created: 1621006125043
---

Pasting an old recipee from ZettelKasten



Linked to [[202002251433]] in silico fragmentation worflow.

Children workflow on the beast MAPP 


Side notes : try to write everything as scripts so that they can be launched without a GUI (ex on X2Go or directly Boabab).


# Tutorial for NPatlas in silico fragmentation data treatment


## Prior to fragmentation 

### Prepare space delimited input file

Complete metadate file is converted to list of Unique ID and smiles space separated (for cfm id input)

python frag_list_preparator.py ../npatlas_data/np_atlas_2019_12.tsv ../npatlas_data/np_atlas_2019_12_for_frag.tsv NPAID SMILES

python frag_list_preparator.py ../open_np_db_data/open_NP_db.tsv ../open_np_db_data/open_NP_db_tofrag.txt shortinchikey shortinchikey smiles

### Split the file

(Works on Linux based shells)

split -a 5 -l 500 -d ../open_np_db_data/open_NP_db_tofrag.txt ../open_np_db_data/opennpdb_tofrag/opennpdb_
split -a 5 -l 500 -d ./lotus_data/lotus_data_for_frag.txt ./lotus_data/lotus_data_for_frag/lotus_data_

split -a 5 -l 500 -d ./ ./lotus_data/lotus_data_for_frag/lotus_data_
split -a 5 -l 500 -d cfm/cfm_input/platinum_tofrag.tsv cfm/cfm_input/splitted/lotus_to_frag_

This one allows to preserve extensions and is build on number of desired chunks without splitting lines
split -a 5 -n l/199 -d --additional-suffix=.txt  cfm_input/sub_platinum_tofrag.tsv cfm_input/splitted/lotus_to_frag_

### When using the docker cli files need to have an extension (or taken as folder ?)

for f in *; do mv "$f" "$f.txt"; done

if you made a mistacke 

find / -type f -name '*.txt' -exec sh -c 'mv -- "$0" "${0%.txt}"' {} \;

### Prepare mutilple bash file to launch on baobab

(strangely enough the .sh incrementer script return an error on Linux, runned OK on MacOS command line )

Note: apparently sbatch as been replaced by srun on the boabab server side. Be sure to update the scripts accordingly



## Fetching cfm-predict results

Download cfm-predict fragmentation results from the baob server using rsync command

rsync -rvz -e 'ssh' --progress allardp@baobab2.unige.ch:/home/allardp/CFM_results/npatlas ./results
rsync -rvz -e 'ssh' --progress allardp@baobab2.unige.ch:/home/allardp/CFM_results/coconut/ .

find ./ -type f -name '*.mgf' | wc  


allows to count all file in a folder 
Here 25090 files for NPatalas

Coconut 384222 .log files


 384150 mgf files


## We might eventually need to move all files from subfolders recursively to a superior folder

find ./bacasable -type f -print0 | xargs -0 mv -t ./bacasable



find ./results_coconut -type f -print0 | xargs -0 mv -t ./results_coconut


## Pruning the raw log files

The output of cfm-predict consist of .log file containing mass spectra, where each fragments are individually labelled and eventually linked to a substrcture. Such information might be usefull later but for now we only want to keep the raw ms data

(need to define a help function here)

python raw_log_treater_npatlas.py ../npatlas_data/results_npatlas/npatlas/ .log
python raw_log_treater.py ../coconut_data/results_coconut/ .log



At this step .log file should be pruned and contains only digits (m/z and intensities)


for coconut Parsing directory../coconut_data/results_coconut/ with file extension :.log

'mass' ../coconut_data/results_coconut/CNP0402147.log
'mass' ../coconut_data/results_coconut/CNP0153817.log
'mass' ../coconut_data/results_coconut/CNP0155980.log
'mass' ../coconut_data/results_coconut/CNP0086807.log
'mass' ../coconut_data/results_coconut/CNP0199206.log
'mass' ../coconut_data/results_coconut/CNP0334817.log
'mass' ../coconut_data/results_coconut/CNP0366374.log
'mass' ../coconut_data/results_coconut/CNP0232712.log
'mass' ../coconut_data/results_coconut/CNP0370068.log
'mass' ../coconut_data/results_coconut/CNP0055178.log
'mass' ../coconut_data/results_coconut/CNP0228597.log
'mass' ../coconut_data/results_coconut/CNP0119974.log
'mass' ../coconut_data/results_coconut/CNP0132139.log
'mass' ../coconut_data/results_coconut/CNP0145457.log
'mass' ../coconut_data/results_coconut/CNP0230801.log
'mass' ../coconut_data/results_coconut/CNP0310370.log
'mass' ../coconut_data/results_coconut/CNP0149436.log
'mass' ../coconut_data/results_coconut/CNP0396848.log
'mass' ../coconut_data/results_coconut/CNP0401434.log
'mass' ../coconut_data/results_coconut/CNP0101561.log
'mass' ../coconut_data/results_coconut/CNP0390928.log
'mass' ../coconut_data/results_coconut/CNP0405256.log
'mass' ../coconut_data/results_coconut/CNP0395006.log
'mass' ../coconut_data/results_coconut/CNP0159145.log
'mass' ../coconut_data/results_coconut/CNP0131085.log
'mass' ../coconut_data/results_coconut/CNP0230696.log
'mass' ../coconut_data/results_coconut/CNP0014450.log
'mass' ../coconut_data/results_coconut/CNP0214739.log
'mass' ../coconut_data/results_coconut/CNP0302005.log
'mass' ../coconut_data/results_coconut/CNP0279314.log
'mass' ../coconut_data/results_coconut/CNP0177036.log
'mass' ../coconut_data/results_coconut/CNP0274256.log
'mass' ../coconut_data/results_coconut/CNP0403745.log
'mass' ../coconut_data/results_coconut/CNP0039287.log
'mass' ../coconut_data/results_coconut/CNP0238803.log
'mass' ../coconut_data/results_coconut/CNP0014261.log
'mass' ../coconut_data/results_coconut/CNP0077076.log
'mass' ../coconut_data/results_coconut/CNP0125300.log
'mass' ../coconut_data/results_coconut/CNP0228582.log
'mass' ../coconut_data/results_coconut/CNP0393136.log
'mass' ../coconut_data/results_coconut/CNP0338003.log
'mass' ../coconut_data/results_coconut/CNP0070182.log
'mass' ../coconut_data/results_coconut/CNP0230961.log
'mass' ../coconut_data/results_coconut/CNP0001326.log
'mass' ../coconut_data/results_coconut/CNP0088652.log
'mass' ../coconut_data/results_coconut/CNP0045797.log
'mass' ../coconut_data/results_coconut/CNP0175458.log
'mass' ../coconut_data/results_coconut/CNP0300969.log
'mass' ../coconut_data/results_coconut/CNP0030335.log
'mass' ../coconut_data/results_coconut/CNP0126194.log
'mass' ../coconut_data/results_coconut/CNP0334816.log
'mass' ../coconut_data/results_coconut/CNP0290616.log
'mass' ../coconut_data/results_coconut/CNP0386127.log
'mass' ../coconut_data/results_coconut/CNP0406328.log
'mass' ../coconut_data/results_coconut/CNP0127289.log
'mass' ../coconut_data/results_coconut/CNP0032755.log
'mass' ../coconut_data/results_coconut/CNP0258640.log
'mass' ../coconut_data/results_coconut/CNP0199475.log
'mass' ../coconut_data/results_coconut/CNP0350989.log
'mass' ../coconut_data/results_coconut/CNP0333350.log
'mass' ../coconut_data/results_coconut/CNP0213544.log
'mass' ../coconut_data/results_coconut/CNP0204567.log
'mass' ../coconut_data/results_coconut/CNP0148525.log
'mass' ../coconut_data/results_coconut/CNP0053639.log
'mass' ../coconut_data/results_coconut/CNP0118368.log
'mass' ../coconut_data/results_coconut/CNP0226584.log
'mass' ../coconut_data/results_coconut/CNP0254221.log
'mass' ../coconut_data/results_coconut/CNP0241364.log
'mass' ../coconut_data/results_coconut/CNP0348684.log
'mass' ../coconut_data/results_coconut/CNP0053255.log
'mass' ../coconut_data/results_coconut/CNP0167909.log
'mass' ../coconut_data/results_coconut/CNP0142603.log
Treated 384150 files, skipped 72






## Populating the mgf headers

### Preparation of the adducted metadata table

We need to prepare and adducted dataframe containing the protonated and deprotonated masses

This script recquire rdkit so we build a environment.yml file from a dedicated conda env

conda env export -n conda-env -f /path/to/environment.yml

Eventually you need to fetch the file from the internet (use wget )

wget https://zenodo.org/record/3547718/files/COCONUT4MetFrag.csv?download=1

Sometimes since SMILES or INchi can yield error and since there is a MF field, the emass can be calculated directly form the MF as described here 
<https://bioinformatics.stackexchange.com/a/9273>. Noooop actually not working since the GetMass() function yield a molecular weight and not and exact mass ....


Script table_adducter_script.py is adapted to cope with different delimiters ... beware and note that $ is mandatory to input the tab delim

python table_adducter_npatlas_script.py ../npatlas_data/np_atlas_2019_12.tsv ../npatlas_data/np_atlas_2019_12_adducted.tsv

python table_adducter_script.py ../coconut_data/COCONUT4MetFrag.csv ',' ../coconut_data/COCONUT4MetFrag_adducted.csv $'\t'


### Addition of the metadata to the individual mgf headers

We can now populate each raw mgf with its corresponding metadata. For this we use the treat_npatlas.py script

python treat_npatlas.py ../npatlas_data/np_atlas_2019_12_adducted.tsv ../npatlas_data/results_npatlas/npatlas/

python mgf_header_populater.py ../coconut_data/COCONUT4MetFrag_adducted.csv ../coconut_data/results_coconut/ Identifier



on coconut 

Treated 384150 files, skipped 28161.




## Generating the final spectral file

We concatenate each documented mgf files to a single spectral mgf file.

find ./ -type f -name '*.mgf' | while read F; do cat ${F} >> ../../npatlas_ISDB_pos.mgf; done
find ./ -type f -name '*.mgf' | while read F; do cat ${F} >> ../../coconut_ISDB_pos.mgf; done


## Outputting non-fragmented entries

For several reasons (charged compounds, some tautomers, structures too heavy to be fragmented in a reasonable amount of time) some entries might not have been fragmented. 

To find them we will first list all correctly converted mgf

find ./ -type f -name '*.mgf' | sed 's!.*/!!' | sed 's!^!!' >  list_mgf.txt

%%here eventually without the extension

find ./ -type f -name '*.mgf' | sed 's!.*/!!' | sed 's!.mgf!!' >  ../../list_mgf.txt

And then the list is compared to the initial input using the table_comparator.py 

python table_comparator.py ../npatlas_data/npatlas_for_frag.txt ../npatlas_data/list_mgf.txt ../npatlas_data/unfragged_list.txt


### check molVS for structure standardization

https://molvs.readthedocs.io/en/latest/index.html
