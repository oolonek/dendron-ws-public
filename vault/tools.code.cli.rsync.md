---
id: SS0rQYcsKz30tWG5tQVOB
title: Rsync
desc: ''
updated: 1702019652135
created: 1609680294356
---

Note : pasted from ZK sublime ()

Sub [[202002291826]] terminal and unix shortcuts


# local > x2go 

```bash
rsync -rvz -e 'ssh -p 80' --progress ./ allardp@x2go.epgl-geneve.org:/home/EPGL.UNIGE.LOCAL/allardp/pybatchclassyfire/
rsync -rvz -e 'ssh -p 80' --progress ./ allardp@x2go.epgl-geneve.org:/home/EPGL.UNIGE.LOCAL/allardp/
pybatchclassyfire/
rsync -rvz -e 'ssh' --progress ./ allardp@10.25.88.39:/home/EPGL.UNIGE.LOCAL/allardp/
rsync -rvz -e 'ssh' --progress ./ allardp@10.25.88.39:/home/EPGL.UNIGE.LOCAL/allardp/opennaturalproductsdb/data/interim/tables/3_curated/

rsync -rvz -e 'ssh' --progress ./ allardp@x2go.epgl-geneve.org:/home/farma.unige.ch/allardp/Desktop/FARMAnetwork/RECHERCHE/COMMON\ FASIE-FATHO/PMA/Ubuntu_VM_img/ISDB_DNP/results
rsync -rvz -e 'ssh' --progress ./ allardp@x2go.epgl-geneve.org:/home/farma.unige.ch/allardp/Desktop/FARMAnetwork/RECHERCHE/COMMON\ FASIE-FATHO/PF_project
rsync -rvz -e 'ssh' --progress ./ allardp@x2go.epgl-geneve.org:/home/farma.unige.ch/allardp/is_fragmentation/lotus_data
```

# local > baobab

```bash
rsync -rvz -e 'ssh' --progress ./opennpdb_tofrag allardp@baobab2.unige.ch:/home/allardp/data_to_frag/opennpdb/
rsync -rvz -e 'ssh' --progress ./ allardp@baobab2.unige.ch:/home/allardp/bash_files/opennpdb_bash

rsync -rvz -e 'ssh' --progress ./ allardp@baobab2.hpc.unige.ch:/home/allardp/bash_files/lotus_bash
rsync -rvz -e 'ssh' --progress ./ allardp@baobab2.hpc.unige.ch:/home/allardp/data_to_frag/lotus/


rsync -rvz -e 'ssh' --progress ./ allardp@baobab2.hpc.unige.ch:/home/allardp/is_fragmentation/lotus_data/

```

# local > beast
nda
```bash
rsync -rvz -e 'ssh' --progress ./ allardpm@biolpc045600:/home/allardpm/data_to_frag/opennpdb/
rsync -rvz -e 'ssh' --progress ./ allardpm@biolpc045600:/home/allardpm/cfm/bash_files
rsync -rvz -e 'ssh' --progress ./Downloads/forticlient_vpn_7.0.7.0246_amd64.deb allardpm@biolpc045600:/home/allardpm/Downloads/
rsync -rvz -e 'ssh' --progress ./Downloads/structures_metadata.db allardpm@biolpc045600:/home/ENPKG/data/structures_db/

```



# beast > local

```bash
rsync -rvz -e 'ssh' --progress allardpm@biolpc045600:/home/allardpm/sandbox/GNPS_output_Qemistree_set/*.qza ./ 

rsync -rvz -e 'ssh' --progress allardpm@biolpc045600:/home/allardpm/sandbox/GNPS_output_Qemistree_set/*.qza ./ 

rsync -rvz -e 'ssh' --progress allardpm@biolpc045600:/home/allardpm/Downloads/wetransfer_rhino_2022-01-10_0411.zip ./ 

rsync -rvz -e 'ssh' --progress allardpm@biolpc045600:/home/allardpm/graphdb-import ./graphdb-import 


# to fetch all file with a given extension. See https://stackoverflow.com/a/11111793 for details

rsync -rvz -e 'ssh' --include="*/" --include="*.qza" --exclude="*" --progress allardpm@biolpc045600:/home/allardpm/sandbox/GNPS_output_Qemistree_set/ ./
```


# x2go > local 

```bash
rsync -rvz -e 'ssh -p 80' --progress allardp@x2go.epgl-geneve.org:/home/EPGL.UNIGE.LOCAL/allardp/is_fragmentation/coconut_data/coconut_ISDB_pos.mgf /Users/pma/Dropbox/People/Swap_MS/ISDB_Coconut
rsync -rvz -e 'ssh -p 80' --progress allardp@x2go.epgl-geneve.org:/home/EPGL.UNIGE.LOCAL/allardp/opennaturalproductsdb/1_databases/PLANTCYC/2_chemo/2_rdkit/PLANTCYC_chemo_rdkit_new_pm.tsv ./
rsync -rvz -e 'ssh -p 80' --progress allardp@x2go.epgl-geneve.org:/home/EPGL.UNIGE.LOCAL/allardp/opennaturalproductsdb/1_databases/PLANTCYC/2_chemo/2_rdkit/PLANTCYC_chemo_rdkit_sanitized_pm.tsv ./
rsync -rvz -e 'ssh -p 80' --progress allardp@x2go.epgl-geneve.org:/home/EPGL.UNIGE.LOCAL/allardp/opennaturalproductsdb/outputs/tables/3_curated/curated_tablesampled1000.tsv ./
rsync -rvz -e 'ssh -p 80' --progress allardp@x2go.epgl-geneve.org:/home/EPGL.UNIGE.LOCAL/allardp/opennaturalproductsdb/outputs/tables/3_curated/curatedTable5000_shuffled_headed ./
rsync -rvz -e 'ssh -p 80' --progress allardp@x2go.epgl-geneve.org:/home/EPGL.UNIGE.LOCAL/allardp/qiime2_cscs_explo_remote/pfabre/cscs_PCoA.qzv ./
rsync -rvz -e 'ssh' --progress allardp@10.25.88.39:/home/EPGL.UNIGE.LOCAL/allardp/opennaturalproductsdb/data/interim/tables/1_translated/structure/unique.tsv ./

rsync -rvz -e 'ssh' --progress allardp@10.25.88.39:/home/EPGL.UNIGE.LOCAL/allardp/opennaturalproductsdb/data/interim/tables_min/3_curated/smiles.gz ./

rsync -rvz -e 'ssh' --progress --include '*.txt' allardp@10.25.88.39:/home/EPGL.UNIGE.LOCAL/allardp/opennaturalproductsdb/data/interim/tables/3_curated/ ./

rsync -rvz -e 'ssh -p 80' --progress allardp@x2go.epgl-geneve.org:/home/EPGL.UNIGE.LOCAL/allardp/Desktop/FARMAnetwork/RECHERCHE/COMMON\ FASIE-FATHO/Workshop_Material/Data_annotation_Workshop_2019/190225_FullDNP_prot_deprot.csv ./


rsync -rvz -e 'ssh' --progress "allardp@x2go.epgl-geneve.org:/home/farma.unige.ch/allardp/Desktop/FARMAnetwork/RECHERCHE/COMMON\ FASIE-FATHO/PMA/Ubuntu_VM_img/ISDB_DNP/results/fbmn_lena_metabo_results_DNP_top50.out" ./ 

rsync -rvz -e 'ssh' --progress "allardp@x2go.epgl-geneve.org:/home/farma.unige.ch/allardp/lotusProcessor/data/interim/tables/4_analysed/platinum.tsv.gz" ./ 

rsync -rvz -e 'ssh' --progress "allardp@x2go.epgl-geneve.org:/home/farma.unige.ch/allardp/lotusProcessor/data/processed/lotus.sqlite" ./ 

rsync -rvz -e 'ssh' --progress "allardp@x2go.epgl-geneve.org:/home/farma.unige.ch/allardp/Documents/Toy_Dataset_MN/GNPS_output_Toy_Dataset_MN/cscs_PCoA.qzv" ./ 


rsync -rvz -e 'ssh' --progress "allardp@x2go.epgl-geneve.org:/home/farma.unige.ch/allardp/Documents/PF_GNP3/GNPS_output_PF_GNP3/feature_table_for_biom.tsv" ./ 





```


# baobab > local 

```bash
rsync -rvz -e 'ssh' --progress allardp@baobab2.unige.ch:/home/allardp/CFM_results/npatlas ./results
rsync -rvz -e 'ssh' --progress allardp@baobab2.unige.ch:/home/allardp/CFM_results/npatlas ./results
rsync -rvz -e 'ssh' --progress allardp@baobab2.unige.ch:/home/allardp/CFM_results/coconut ./ --apend
```

# metabomaps > local 



rsync -rvz -e 'ssh' --progress --rsync-path="sudo rsync" ~/Downloads/wetransfer-27d788/210523_lotus_map4_2D.js pma@metabomaps.nprod.net:/srv/metabo-store/tmap


# local > metabomaps

rsync -rvz -e 'ssh' --progress --rsync-path="sudo rsync" /Users/pma/Dropbox/UniFr/Projects/Ongoing/COMMONS/NPKB/004_rdf/pos pma@metabomaps.nprod.net:/home/pma/graphdb/home/graphdb-import

rsync -rvz -e 'ssh' --progress /Users/pma/Dropbox/UniFr/Projects/Ongoing/COMMONS/NPKB/004_rdf/pos pma@metabomaps.nprod.net:/home/pma/graphdb-import

rsync -rvz -e 'ssh' --progress /Users/pma/Downloads/ pma@metabomaps.nprod.net:/home/pma/Downloads








rsync -rvz -e 'ssh' --progress /Volumes/COMMON\ FASIE-FATHO/PF_project/Graph_organization/7_full_pos_neg ./01_large_files


https://ostechnix.com/how-to-resume-partially-downloaded-or-transferred-files-using-rsync/