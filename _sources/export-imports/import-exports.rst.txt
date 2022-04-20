Import and Export Examples
============================

This is a tutorial of how to do a qiime2 export and import.

Qiime Imports
-------------

Raw Data Example:

``qiime tools import --input-path rawData.tsv --input-format PepsirfContingencyTSVFormat 
--type 'FeatureTable[RawCounts]' --output-path rawData.qza``

Bins Example:

``qiime tools import --input-path bins.tsv --input-format PeptideBinFormat 
--type 'PeptideBins' --output-path bins.qza``

Enriched Directory Example:

``qiime tools import --input-path enriched-dir/ --input-format EnrichedPeptideDirFmt 
--type 'PairwiseEnrichment' --output-path enriched-dir.qza``


Qiime Exports
-------------

Raw Data Example:

``qiime tools export --input-path rawData.qza --output-path rawData.tsv --output-format PepsirfContingencyTSVFormat``

Bins Example:

``qiime tools export --input-path bins.qza --output-path bins.tsv --output-format PeptideBinFormat``

Enriched Directory Example:

``qiime tools export --input-path enriched-dir.qza --output-path enriched-dir/ --output-format EnrichedPeptideDirFmt``
