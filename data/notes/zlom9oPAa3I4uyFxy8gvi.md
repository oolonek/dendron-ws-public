
# A Qiime recipee for Empress display of the pf_project

## Required inputs

- [ ] a feature table (mzmine output)
- [ ] a sample metadata table
- [ ] a feature metadata table

Beware of the confusion between samples and features. In Qiime features refer to OTU and thus have an assigned taxonomy. I our case we have the taxonomy assigned to the samples.




# First we deal with the tree file

qiime tools import \
  --input-path otol_tree_rooted.tre \
  --output-path otol_tree_rooted.qza \
  --type 'Phylogeny[Rooted]'

# the we deal with the feature table 

## First we use biom to convert the tsv to the biom format 
biom convert \
-i feature_table.tsv \
-o feature_table.biom \
--table-type="OTU table" \
--to-hdf5

## Conversion to qiime featureTable

qiime tools import \
--type 'FeatureTable[Frequency]' \
--input-path feature_table.biom \
--output-path feature_table.qza

## We EMPRESS the whole shit
  
qiime empress community-plot \
  --i-tree otol_tree_rooted.qza \
  --i-feature-table feature_table.qza \
  --m-sample-metadata-file sample_metadata.tsv \
  --m-feature-metadata-file feature_taxa.tsv \
  --o-visualization empress-tree.qzv \
  --p-filter-missing-features \
  --p-ignore-missing-samples


Sadly we get the follwoing message

Plugin error from empress:

  At least one non-root branch of the tree must have a positive length.


We thus try to compute branch lenght in R using the ape package

# we infer branch lenght

taxa_tree <-compute.brlen(taxa_tree)
taxa_tree <- read.tree('Dropbox/Research_UNIGE/git_repos/qiime-empress-formatter/src/python/otol_tree.tre')

# we root the tree

# wd_tree_len_rooted <- root(wd_tree_len, outgroup = "Methanobacterium", resolve.root = TRUE)

is.rooted(taxa_tree)


write.tree(taxa_tree, '~/tmp/empress-tutorial/ecometabo_toyset/ecometabo_taxa_tree_rooted.tree')

write.tree(taxa_tree, 'Dropbox/Research_UNIGE/git_repos/qiime-empress-formatter/src/python/otol_tree_rooted.tre')


# Lets add some metadata for the feature table viz

qiime feature-table summarize \
  --i-table feature_table.qza \
  --o-visualization feature_table_viz.qzv \
  --m-sample-metadata-file sample_metadata.tsv

## metadata viz

qiime metadata tabulate \
  --m-input-file sample_metadata.tsv \
  --o-visualization sample_metadata.qzv

## lets try some metadat based filtering of the feature table

qiime feature-table filter-samples \
  --i-table feature_table.qza \
  --m-metadata-file sample_metadata.tsv \
  --p-where "[Taxonomical_Score_ISDB]>0" \
  --o-filtered-table taxscore-filtered-feature_table.qza


qiime feature-table filter-samples \
  --i-table feature-contingency-filtered-table.qza \
  --m-metadata-file sample_metadata.tsv \
  --p-where "[Consensus_class_ci_cf]!='nan'" \
  --o-filtered-table nan-filtered-table.qza


qiime empress community-plot \
  --i-tree otol_tree_rooted.qza \
  --i-feature-table taxscore-filtered-feature_table.qza \
  --m-sample-metadata-file sample_metadata.tsv \
  --m-feature-metadata-file feature_taxa.tsv \
  --m-feature-metadata-file metadata_otoled.tsv \
  --o-visualization empress-tree.qzv \
  --p-filter-missing-features \
  --p-ignore-missing-samples


