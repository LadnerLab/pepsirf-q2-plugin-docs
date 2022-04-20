Import and Export File Format Tables
====================================

This is the place where you will find all file inputs and types for imports and exports.

Qiime Import Table
--------------------

================================== ============================ =================================
            Type of Data                     --input-format arg               --type arg 
================================== ============================ =================================
Raw Data                           PepsirfContingencyTSVFormat  'FeatureTable[RawCounts]'
Normalized Col-sum                 PepsirfContingencyTSVFormat  'FeatureTable[Normed]'
Normalized Difference              PepsirfContingencyTSVFormat  'FeatureTable[NormedDifference]'
Normalized Difference Ratio        PepsirfContingencyTSVFormat  'FeatureTable[NormedDiffRatio]'
Normalized Ratio                   PepsirfContingencyTSVFormat  'FeatureTable[NormedRatio]'
Normalized Sized                   PepsirfContingencyTSVFormat  'FeatureTable[NormedSized]'
Zscores                            PepsirfContingencyTSVFormat  'FeatureTable[Zscore]'
Zscores Nan                        ZscoreNanFormat              'ZscoreNan'
Bins                               PeptideBinFormat             'PeptideBins'
Enrich Thresholds                  EnrichThreshFileFormat       'EnrichThresh'
Num. of Samples                    PepsirfInfoSNPNFormat        'InfoSNPN'
Num. of Peptides                   PepsirfInfoSNPNFormat        'InfoSNPN'
Sum of Probes                      PepsirfInfoSumOfProbesFmt    'InfoSumOfProbes'
Multi-File                         SubjoinMultiFileFmt          'MultiFile'
Protein Fasta                      ProteinFastaFmt              'ProteinFasta'
Peptide Fasta                      PeptideFastaFmt              'PeptideFasta'
Link Output                        PepsirfLinkTSVFormat         'Link'
Enriched Dir                       EnrichedPeptideDirFmt        'PairwiseEnrichment'
Enriched Peptide List              PeptideIDListFmt             'PeptideIDList'
.DMP file                          PepsirfDMPFormat             'PepsirfDMP'
Deconv Singluar                    PepsirfDeconvSingularFormat  'DeconvSingular'
Deconv Batch Dir                   PepsirfDeconvBatchDirFmt     'DeconvBatch'
Score Per Round (Deconv)           ScorePerRoundDirFmt          'ScorePerRound'
Peptide Assignment Map (Deconv)    PeptideAssignMapDirFmt       'PeptideAssignmentMap'
fif file (Demux)                   PepsirfDemuxFifFmt           'DemuxFif'
Sample List (Demux)                PepsirfDemuxSampleListFmt    'DemuxSampleList'
Index (Demux)                      PepsirfDemuxIndexFmt         'DemuxIndex'
Library (Demux)                    PepsirfDemuxLibraryFmt       'DemuxLibrary'
FASTQ file (Demux)                 PepsirfDemuxFastqFmt         'DemuxFastq'
Diagnostic file (Demux)            PepsirfDemuxDiagnosticFormat 'DemuxDiagnostic'
Protein Alignment (proteinHeatmap) ProteinAlignmentDirFormat    'ProteinAlignment'
Mutant Reference file              MutantReferenceFileFmt       'MutantReference'
================================== ============================ =================================

Qiime Export Table
------------------

================================== ============================
            Type of Data               --output-format arg
================================== ============================
Raw Data                           PepsirfContingencyTSVFormat
Normalized Col-sum                 PepsirfContingencyTSVFormat
Normalized Difference              PepsirfContingencyTSVFormat
Normalized Difference Ratio        PepsirfContingencyTSVFormat
Normalized Ratio                   PepsirfContingencyTSVFormat
Normalized Sized                   PepsirfContingencyTSVFormat
Zscores                            PepsirfContingencyTSVFormat
Zscores Nan                        ZscoreNanFormat
Bins                               PeptideBinFormat
Enrich Thresholds                  EnrichThreshFileFormat
Num. of Samples                    PepsirfInfoSNPNFormat
Num. of Peptides                   PepsirfInfoSNPNFormat
Sum of Probes                      PepsirfInfoSumOfProbesFmt
Multi-File                         SubjoinMultiFileFmt
Protein Fasta                      ProteinFastaFmt
Peptide Fasta                      PeptideFastaFmt
Link Output                        PepsirfLinkTSVFormat
Enriched Dir                       EnrichedPeptideDirFmt
Enriched Peptide List              PeptideIDListFmt
.DMP file                          PepsirfDMPFormat
Deconv Singluar                    PepsirfDeconvSingularFormat
Deconv Batch Dir                   PepsirfDeconvBatchDirFmt
Score Per Round (Deconv)           ScorePerRoundDirFmt
Peptide Assignment Map (Deconv)    PeptideAssignMapDirFmt
fif file (Demux)                   PepsirfDemuxFifFmt
Sample List (Demux)                PepsirfDemuxSampleListFmt
Index (Demux)                      PepsirfDemuxIndexFmt
Library (Demux)                    PepsirfDemuxLibraryFmt
FASTQ file (Demux)                 PepsirfDemuxFastqFmt
Diagnostic file (Demux)            PepsirfDemuxDiagnosticFormat
Protein Alignment (proteinHeatmap) ProteinAlignmentDirFormat
Mutant Reference file              MutantReferenceFileFmt
================================== ============================
