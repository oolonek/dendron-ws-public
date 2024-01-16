---
id: cO1TjrEicNPknM4qFPBm1
title: Cscs
desc: ''
updated: 1705413507861
created: 1606994034189
---

# qiime CSCS cookbook

# bioinfo_qiime2_cscs_workflow
tags = #bioinfo #recipee #tutorial #qiime

List of commands and recippe for a qiime2 cscs project

qiime2
<https://docs.qiime2.org/2020.2/getting-starte
qiime cscs 
<https://github.com/madeleineernst/q2-cscs#2-compute-the-chemical-structural-and-compositional-dissimilarity-for-a-real-world-dataset>


download the GNPS job

Mind the DownloadResult?task= string !!!

`curl -d "" 'https://gnps.ucsd.edu/ProteoSAFe/DownloadResult?task=5729dd0f7a47475abc879e164c237f56&view=download_cluster_buckettable' -o GNPS_output.zip`

fetch the metadata table :

`cp GNPS_output/quantification_table_reformatted/d6548148e7e040bb8d573bc6d4954d4b.csv GNPS_buckettable.csv`


eventually remove some columns see [[20200611160123]] terminal_directly_cut_csv_column

`cut --complement -f 2,3 -d, GNPS_buckettable.csv > GNPS_buckettable_tomod.csv`

then convert from csv to tsv see [[20200611161504]] terminal_convert_csv_to_tsv

`cat GNPS_buckettable_tomod.csv | tr "," "\\t" > GNPS_buckettable.tsv`

you can now convert to BIOM format 

`biom convert -i GNPS_buckettable.tsv -o GNPS_buckettable.biom --table-type="OTU table" --to-hdf5

run using cpus 


time qiime cscs cscs --p-css-edges GNPS_edges.tsv --i-features GNPS_buckettable.qza --p-cosine-threshold 0.7 --p-normalization --p-cpus 40 --o-distance-matrix cscs_distance_matrix.qza



###########
Brutal command line history

2664  source activate qiime2-2020.2
 2665  qiime cscs cscs --p-css-edges small_GNPS_edges.tsv --i-features small_GNPS_buckettable.qza --p-cosine-threshold 0.5 --p-normalization --o-distance-matrix small_cscs_distance_matrix.qza
 2666  ls
 2667  wget https://raw.githubusercontent.com/madeleineernst/q2-cscs/master/tests/data/small_GNPS_buckettable.qza
 2668  wget https://raw.githubusercontent.com/madeleineernst/q2-cscs/master/tests/data/small_GNPS_edges.tsv
 2669  qiime cscs cscs --p-css-edges small_GNPS_edges.tsv --i-features small_GNPS_buckettable.qza --p-cosine-threshold 0.5 --p-normalization --o-distance-matrix small_cscs_distance_matrix.qza
 2670  qiime tools view cscs_PCoA.qzv
 2671  qiime tools view cscs_PCoA.qza
 2672  ls -larts
 2673  biom convert -i GNPS_buckettable.tsv -o GNPS_buckettable.biom --table-type="OTU table" --to-hdf5
 2674  qiime tools import --type 'FeatureTable[Frequency]' --input-path GNPS_buckettable.biom --output-path GNPS_buckettable.qza
 2675  qiime cscs cscs --p-css-edges GNPS_edges.tsv --i-features GNPS_buckettable.qza --p-cosine-threshold 0.5 --p-normalization --o-distance-matrix cscs_distance_matrix.qza
 2676  qiime cscs cscs
 2677  qiime cscs cscs --p-css-edges GNPS_edges.tsv --i-features GNPS_buckettable.qza --p-cosine-threshold 0.5 --p-normalization --p-cpus 4 --o-distance-matrix cscs_distance_matrix.qza
 2678  htop
 2679  qiime diversity pcoa --i-distance-matrix cscs_distance_matrix.qza --o-pcoa cscs_PCoA.qza
 2680  qiime emperor plot --i-pcoa cscs_PCoA.qza --m-metadata-file MappingFile_UrineSamples.txt --o-visualization cscs_PCoA.qzv
 2681  qiime tools view cscs_PCoA.qzv
 2682  qiime diversity beta --i-table GNPS_buckettable.qza  --p-metric braycurtis --o-distance-matrix braycurtis_GNPS_buckettable.qza
 2683  qiime diversity pcoa --i-distance-matrix braycurtis_GNPS_buckettable.qza --o-pcoa braycurtis_PCoA.qza
 2684  qiime emperor plot --i-pcoa braycurtis_PCoA.qza --m-metadata-file MappingFile_UrineSamples.txt --o-visualization braycurtis_PCoA.qzv
 2685  qiime tools view braycurtis_PCoA.qzv
 2686  qiime diversity mantel --i-dm1 cscs_distance_matrix.qza --i-dm2 braycurtis_GNPS_buckettable.qza --o-visualization mantel.qzv
 2687  qiime diversity procrustes-analysis --i-reference braycurtis_PCoA.qza --i-other cscs_PCoA.qza --output-dir ./procrustes-out
 2688  qiime emperor procrustes-plot --i-reference-pcoa procrustes-out/transformed_reference.qza --i-other-pcoa procrustes-out/transformed_other.qza --m-metadata-file MappingFile_UrineSamples.txt --o-visualization procrustes-out/plot.qzv
 2689  qiime tools view procrustes-out/plot.qzv
 2690  ls -lart
 2691  cd erythroxylum
 2692  ls
 2693  biom convert -i GNPS_buckettable.tsv -o GNPS_buckettable.biom --table-type="OTU table" --to-hdf5
 2694  qiime tools import --type 'FeatureTable[Frequency]' --input-path GNPS_buckettable.biom --output-path GNPS_buckettable.qza
 2695  qiime cscs cscs --p-css-edges GNPS_edges.tsv --i-features GNPS_buckettable.qza --p-cosine-threshold 0.7 --p-normalization -p-cpus 6 --o-distance-matrix cscs_distance_matrix.qza
 2696  qiime cscs cscs --p-css-edges GNPS_edges.tsv --i-features GNPS_buckettable.qza --p-cosine-threshold 0.7 --p-normalization --p-cpus 6 --o-distance-matrix cscs_distance_matrix.qza
 2697  ssh x2go.epgl-geneve.org -p 80
 2698  ssh allardp@x2go.epgl-geneve.org -p 80
 2699  cd Dropbox/Research_UNIGE/git_repos
 2700  git clone https://github.com/madeleineernst/pyMolNetEnhancer.git
 2701  qiime diversity pcoa --i-distance-matrix cscs_distance_matrix.qza --o-pcoa cscs_PCoA.qza
 2702  ls
 2703  cd GNPS_output
 2704  ls
 2705  cd metadata_table
 2706  ls
 2707  nano metadata_table-00000.txt
 2708  cd ..
 2709  qiime emperor plot --i-pcoa cscs_PCoA.qza --m-metadata-file GNPS_output/metadata_table/metadata_table-00000.txt --o-visualization cscs_PCoA.qzv
 2710  nano GNPS_output/metadata_table/metadata_table-00000.txt
 2711  qiime emperor plot --i-pcoa cscs_PCoA.qza --m-metadata-file GNPS_output/metadata_table/metadata_table-00000.txt --o-visualization cscs_PCoA.qzv
 2712  ls
 2713  nano GNPS_output/metadata_table/metadata_table-00000.txt
 2714  qiime emperor plot --i-pcoa cscs_PCoA.qza --m-metadata-file GNPS_output/metadata_table/metadata_table-00000.txt --o-visualization cscs_PCoA.qzv
 2715  nano GNPS_output/metadata_table/metadata_table-00000.txt
 2716  qiime emperor plot --i-pcoa cscs_PCoA.qza --m-metadata-file GNPS_output/metadata_table/metadata_table-00000.txt --o-visualization cscs_PCoA.qzv
 2717  qiime emperor plot
 2718  qiime emperor plot --i-pcoa cscs_PCoA.qza --m-metadata-file GNPS_output/metadata_table/metadata_table-00000.txt --p-ignore-missing-samples --o-visualization cscs_PCoA.qzv
 2719  qiime tools view cscs_PCoA.qzv
 2720  qiime diversity beta --i-table GNPS_buckettable.qza  --p-metric braycurtis --o-distance-matrix braycurtis_GNPS_buckettable.qza
 2721  qiime diversity pcoa --i-distance-matrix braycurtis_GNPS_buckettable.qza --o-pcoa braycurtis_PCoA.qza
 2722  qiime emperor plot --i-pcoa braycurtis_PCoA.qza --m-metadata-file MappingFile_UrineSamples.txt --o-visualization braycurtis_PCoA.qzv
 2723  qiime emperor plot --i-pcoa braycurtis_PCoA.qza --m-metadata-file GNPS_output/metadata_table/metadata_table-00000.txt --o-visualization braycurtis_PCoA.qzv
 2724  qiime emperor plot --i-pcoa braycurtis_PCoA.qza --m-metadata-file GNPS_output/metadata_table/metadata_table-00000.txt --p-ignore-missing-samples --o-visualization braycurtis_PCoA.qzv
 2725  qiime diversity mantel --i-dm1 cscs_distance_matrix.qza --i-dm2 braycurtis_GNPS_buckettable.qza --o-visualization mantel.qzv
 2726  qiime diversity procrustes-analysis --i-reference braycurtis_PCoA.qza --i-other cscs_PCoA.qza --output-dir ./procrustes-out
 2727  qiime emperor procrustes-plot --i-reference-pcoa procrustes-out/transformed_reference.qza --i-other-pcoa procrustes-out/transformed_other.qza --m-metadata-file GNPS_output/metadata_table/metadata_table-00000.txt --p-ignore-missing-samples --o-visualization procrustes-out/plot.qzv
 2728  qiime tools view procrustes-out/plot.qzv
 2729  ssh allardp@x2go.epgl-geneve.org -p 80
 2730  ls -lkart
 2731  ls -lart
 2732  qiime diversity
 2733  qiime diversity beta-rarefaction
 2734  ls
 2735  qiime tools view cscs_PCoA.qza
 2736  qiime tools view cscs_PCoA.qzv
 2737  qiime tools view procrustes-out/plot.qzv
 2738* ls
 2739* rsync -rvz -e 'ssh -p 80' --progress ./*.mp4 allardp@x2go.epgl-geneve.org:/home/EPGL.UNIGE.LOCAL/allardp/
 2740* htop
 2741* rsync -rvz -e 'ssh -p 80' --progress ./*.mp4 allardp@x2go.epgl-geneve.org:/home/EPGL.UNIGE.LOCAL/allardp/




 ###################################################################################
 ###################################################################################
# Clean Recipee PFproject
 ###################################################################################
 ###################################################################################


We need three inputs
1 - a feature table
2 - a edges table
3 - a metadata table

See qiime2 website for specification of the files. <https://docs.qiime2.org/2020.2/tutorials/metadata/>


After installing enter the dedicated env

source activate qiime2-2020.2


On x2go you might need to resolve your issue by exporting the
following environment variables:

    export LC_ALL=C.UTF-8
    export LANG=C.UTF-8

## Convert your mass spectral feature table to the .qza format

First, convert the .tsv feature table (GNPS_buckettable.tsv) to a .biom feature table (GNPS_buckettable.biom):

`biom convert -i PF_selected_feature_table.tsv -o PF_selected_feature_table.biom --table-type="OTU table" --to-hdf5`

Then convert the .biom feature table (GNPS_buckettable.biom) to a .qza feature table (GNPS_buckettable.qza):

`qiime tools import --type 'FeatureTable[Frequency]' --input-path PF_selected_feature_table.biom --output-path PF_selected_feature_table.qza`

## Compute the chemical structural and compositional dissimilarity metric for all pairs of samples in your feature table

To compute the chemical structural and compositional dissimilarity metric for all pairs of samples in your feature table type:

Note : here we had an extra columns in the tsv so we can drop it directly form the command line 
by 
cut --complement -f 1 PF_selected_edeges.tsv > PF_selected_edeges_ready.tsv


`nohup time qiime cscs cscs --p-css-edges PF_selected_edeges.tsv --i-features PF_selected_feature_table.qza --p-cosine-threshold 0.7 --p-normalization --p-cpus 40 --o-distance-matrix cscs_distance_matrix.qza`


## Update on Dec 2020

Messing around with qiime but keeping the recipe

### Feature table creation 

`biom convert \-i /Users/pma/Dropbox/Research_UNIGE/git_repos/pf_project/data/output/PF_selected_feature_table.tsv  -o PF_selected_feature_table.biom --table-type="OTU table" --to-hdf5`

### if you need to go from biom to tsv 

biom convert -i table.biom -o table.from_biom.txt --to-tsv


### Conversion to qiime featureTable

qiime tools import --type 'FeatureTable[Frequency]' --input-path PF_selected_feature_table.biom --output-path PF_selected_feature_table.qza

### Summarizing 
qiime feature-table summarize \
--i-table PF_selected_feature_table.qza \
--o-visualization table_summarized.qzv

### and having a look at the results

qiime tools view table_summarized.qzv

### Now we'll filter for features present in too many samples

qiime feature-table filter-features \
  --i-table PF_selected_feature_table.qza \
  --p-max-frequency 500 \
  --o-filtered-table feature-frequency-filtered-table.qza

### In fact here e would rather like a contingency filtered table 


qiime feature-table filter-features \
  --i-table PF_selected_feature_table.qza \
  --p-max-samples 500 \
  --o-filtered-table sample-contingency-filtered-table.qza

  
## lets try to make a heatmap out of the previous filtered table

qiime feature-table heatmap \
--i-table sample-contingency-filtered-table.qza \
--o-visualization heatmap.qzv

## lets work on phylogeny import

qiime tools import \
  --input-path pf_collec_newick.tre \
  --output-path pf_collec_newick.qza \
  --type 'Phylogeny[Unrooted]'


# Lets add some metadata for the feature table viz

qiime feature-table summarize \
  --i-table PF_selected_feature_table.qza \
  --o-visualization table.qzv \
  --m-sample-metadata-file pf_metatable_qiimed.tsv


# alpha rarefaction

qiime diversity alpha-rarefaction \
  --i-table PF_selected_feature_table.qza \
  --i-phylogeny pf_collec_newick.qza \
  --p-max-depth 4000 \
  --m-metadata-file pf_metatable_qiimed.tsv \
  --o-visualization alpha-rarefaction.qzv


##metadata viz

qiime metadata tabulate \
  --m-input-file pf_collec_newick_rooted.qza \
  --o-visualization tabulated-feature-metadata.qzv



  ## EMPRESS

  
ecometabo_toyset qiime empress community-plot \
  --i-tree phylogeny.qza \
  --i-feature-table feature_table.qza \
  --m-sample-metadata-file feature_metadata.tsv \
  --m-feature-metadata-file feature_taxa.tsv \
  --o-visualization empress-tree2.qzv \
  --p-filter-missing-features \
  --p-ignore-missing-samples



## QEMISTREE

biom convert -i mzmine_local_quant_formatted.tsv  -o mzmine_local_feature_table.biom --table-type="OTU table" --to-hdf5

qiime tools import --input-path mzmine_local_feature_table.biom --output-path feature-table.qza --type "FeatureTable[Frequency]"

qiime tools import --input-path sirius_local.mgf --output-path sirius.mgf.qza --type MassSpectrometryFeatures

qiime qemistree compute-fragmentation-trees --p-sirius-path 'sirius-osx64-headless-4.0.1/bin/' \
  --i-features sirius.mgf.qza \
  --p-ppm-max 15 \
  --p-profile orbitrap \
  --p-ionization-mode positive \
  --p-java-flags "-Djava.io.tmpdir=~/tmp/ -Xms16G -Xmx32G" \
  --o-fragmentation-trees fragmentation_trees.qza

  qiime qemistree rerank-molecular-formulas --p-sirius-path 'sirius-osx64-headless-4.0.1/bin/' \
  --i-features sirius.mgf.qza \
  --i-fragmentation-trees fragmentation_trees.qza \
  --p-zodiac-threshold 0.95 \
  --p-java-flags "-Djava.io.tmpdir=~/tmp/ -Xms16G -Xmx32G" \
  --o-molecular-formulas molecular_formulas.qza
  
qiime qemistree predict-fingerprints --p-sirius-path 'sirius-osx64-headless-4.0.1/bin/' \
  --i-molecular-formulas molecular_formulas.qza \
  --p-ppm-max 20 \
  --p-java-flags "-Djava.io.tmpdir=~/tmp/ -Xms16G -Xmx32G" \
  --o-predicted-fingerprints fingerprints.qza

qiime qemistree make-hierarchy \
  --i-csi-results fingerprints.qza \
  --i-feature-tables feature-table.qza \
  --o-tree qemistree.qza \
  --o-feature-table feature-table-hashed.qza \
  --o-feature-data feature-data.qza

qiime qemistree get-classyfire-taxonomy \
  --i-feature-data feature-data.qza \
  --o-classified-feature-data classified-merged-feature-data.qza


qiime empress community-plot \
    --i-tree qemistree-tree.qza \
    --i-feature-table feature-table-hashed.qza \
    --m-sample-metadata-file sample-metadata.tsv \
    --m-feature-metadata-file feature-data.qza \
    --o-visualization empress-tree.qzv

