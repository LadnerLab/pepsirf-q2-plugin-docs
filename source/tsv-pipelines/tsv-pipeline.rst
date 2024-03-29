TSV/Dir Pipeline Information
============================

This is information regarding q2-ps-plot's and q2-autopepsirf's TSV/Dir pipelines, 
as well as tutorials on how to use the various tsv/dir pipelines.

Available TSV/Dir pipelines
---------------------------

q2-ps-plot:

================================== ==============================
QZA Modules                        Corresponding TSV/Dir Pipeline
================================== ==============================
mutant_scatter                     *Coming Soon!*
proteinHeatmap                     proteinHeatmap-dir
repScatters                        repScatters-tsv
zenrich                            zenrich-tsv
================================== ==============================

q2-autopepsirf:

================================== ==============================
QZA Modules                        Corresponding TSV/Dir Pipeline
================================== ==============================
diffEnrich                         diffEnrich-tsv
================================== ==============================

TSV/Dir Pipeline Tutorials
--------------------------

Instead of inputting a QZA file in an input (*--i-flag*), a TSV file or directory filepath is inputted into 
a different parameters flag typically ending in "-filepath" (*--p-flag-filepath*).

**proteinHeatmap:**

* QZA Module Example:
  
  ``qiime ps-plot proteinHeatmap --i-enriched-dir enriched-dir.qza --i-protein-alignment alignment.qza 
  --o-visualization proteinHeatmap.qzv``

* TSV/Dir Pipeline Example:
  
  ``qiime ps-plot proteinHeatmap-dir --p-enriched-dir-filepath enriched-dir/ --p-protein-alignment-filepath alignment/ 
  --o-protein-heatmap-vis proteinHeatmap.qzv``

**repScatters:**

* QZA Module Example:
  
  ``qiime ps-plot repScatters --i-zscore some-zscore.qza --m-source-file samples-source.tsv --m-source-column 
  source --o-visualizaion repScatters.qza``

* TSV/Dir Pipeline Example:
  
  ``qiime ps-plot repScatters-tsv --p-zscore-filepath some-zscore.tsv --m-source-file samples-source.tsv --m-source-column 
  source --o-rep-scatters-vis repScatters.qzv``

**zenrich:**

* QZA Module Example:
  
  ``qiime ps-plot zenrich --i-data col-sum.qza --i-zscores zscores.qza --p-negative-id someID --m-source-file 
  samples-source.tsv --m-soure-column source --p-exact-cs-thresh 0 --p-pepsirf-binary pepsirf --o-visualization zenrich.qzv``

* TSV/Dir Pipeline Example:
  
  ``qiime ps-plot zenrich-tsv --p-data-filepath col-sum.tsv --p-zscores-filepath zscores.tsv --p-negative-id someID --m-source-file 
  samples-source.tsv --m-soure-column source --p-exact-cs-thresh 0 --p-pepsirf-binary pepsirf --o-zenrich-vis zenrich.qzv``

**diffEnrich:**

* QZA Module Example:
  
  ``qiime autopepsirf diffEnrich --i-raw-data raw-data.qza --i-bins bins.qza --p-negative-id someID --p-exact-z-thresh 6,10 
  --p-pepsirf-tsv-dir testingTSV/ --p-tsv-base-str baseString --p-hdi 0.95 --p-pepsirf-binary pepsirf 
  --output-dir autopepsirf-diffEnrich``

* TSV/Dir Pipeline Example:
  
  ``qiime autopepsirf diffEnrich-tsv --p-raw-data-filepath raw-data.tsv --p-bins-filepath bins.tsv --p-negative-id 
  someID --p-exact-z-thresh 6,10 --p-pepsirf-tsv-dir testingTSV/ --p-tsv-base-str baseString --p-hdi 0.95 
  --p-pepsirf-binary pepsirf --output-dir autopepsirf-diffEnrich``