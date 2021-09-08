---
id: 4q6R0Wq7vq4KwfN3Ok92J
title: Pf
desc: ''
updated: 1616080924669
created: 1615882210535
---

Tuesday 16 March 2021

Recipee for the PF MN CSCS calculations

First it appears that conda is not present

This https://askubuntu.com/a/1062621 solved the problem
export PATH=~/anaconda3/bin:$PATH


Need to reinstall the latest qiime version sudo wget https://data.qiime2.org/distro/core/qiime2-2021.2-py36-linux-conda.yml

source activate qiime2-2021.2

wget / curl not working (proxy reason most likely on x2go)


We use the peak_list_formatter_cscs.py to get GNPS job and propelry format the quantification tables

`biom convert -i for_biom.tsv -o for_biom.biom --table-type="OTU table" --to-hdf5`



Then convert the .biom feature table to a .qza feature table :

`qiime tools import --type 'FeatureTable[Frequency]' --input-path for_biom.biom --output-path feature_table.qza`

To compute the chemical structural and compositional dissimilarity metric for all pairs of samples in your feature table type:

`nohup time qiime cscs cscs --p-css-edges networkedges_selfloop --i-features quantification_table --p-cosine-threshold 0.7 --p-normalization --p-cpus 40 --o-distance-matrix cscs_distance_matrix.qza`

'time qiime cscs cscs --p-css-edges networkedges_selfloop/31a1340378cd46d7b9f5ebf8afbb2565..selfloop --i-features feature_table.qza --p-cosine-threshold 0.7 --p-normalization --p-cpus 40 --o-distance-matrix cscs_distance_matrix.qza'


'nohup bash -c 'time qiime cscs cscs --p-css-edges networkedges_selfloop/31a1340378cd46d7b9f5ebf8afbb2565..selfloop --i-features feature_table.qza --p-cosine-threshold 0.7 --p-normalization --p-cpus 40 --o-distance-matrix cscs_distance_matrix.qza''


'nohup bash -c 'time qiime cscs cscs --p-css-edges networkedges_selfloop/31a1340378cd46d7b9f5ebf8afbb2565..selfloop --i-features feature_table.qza --p-cosine-threshold 0.7 --p-normalization --p-no-weighted --p-cpus 40 --o-distance-matrix cscs_distance_matrix_unweighed.qza''

nohup bash -c 'time qiime cscs cscs --p-css-edges networkedges_selfloop/3466497461974198a9ab8c9463d05b53..selfloop --i-features feature_table.qza --p-cosine-threshold 0.7 --p-normalization --p-no-weighted --p-cpus 40 --o-distance-matrix cscs_distance_matrix_unweighed.qza'

nohup bash -c 'time qiime cscs cscs --p-css-edges networkedges_selfloop/3466497461974198a9ab8c9463d05b53..selfloop --i-features feature_table.qza --p-cosine-threshold 0.7 --p-normalization --p-cpus 40 --o-distance-matrix cscs_distance_matrix.qza'


Visualize the chemical structural and compositional dissimilarity in interactive PCoA space
To create PCos from the chemical structural and compositional dissimilarity matrix type:

`qiime diversity pcoa --i-distance-matrix cscs_distance_matrix.qza --o-pcoa cscs_PCoA.qza`

To create an interactive ordination plot of the above created PCoA with integrated sample metadata, prepare a metadata file. You can find a metadata file for this example dataset within the Example folder. Make sure that the Sample IDs provided in the metadata file correspond to the Sample IDs in your distance_matrix.qza file. Then type:

Uploading previously generated metadata
rsync -rvz -e 'ssh' --progress ./PF_metadata_qiime.tsv allardp@x2go.epgl-geneve.org:

`qiime emperor plot --i-pcoa cscs_PCoA.qza --m-metadata-file PF_metadata_qiime.tsv --o-visualization cscs_PCoA.qzv`

To visualize the interactive PCoA type:

`qiime tools view cscs_PCoA.qzv`


  --p-normalization / --p-no-normalization
                         Perform Total Ion Current Normalization (TIC) on the
                         feature table                         [default: True]
  --p-weighted / --p-no-weighted
                         Weight CSCS by feature intensity      [default: True]


## Qemistree dataset

https://gnps.ucsd.edu/ProteoSAFe/status.jsp?task=044e981ff0d84246ae5c91ef3db643a8

