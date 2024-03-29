Ps-plot Tutorials - Multiple Interface Edition
==============================================

Description
-----------

This guide is a preview of how you can use some of q2-ps-plot's individual modules.

Introduction
------------

In this tutorial you'll use QIIME 2 to perform an analysis of some data.

Typical Run Time: 1 Minute 30 Seconds

Protein Alignment
-----------------

.. usage-selector::

.. qiime ps-plot proteinHeatmap --i-enriched-dir 10Z-HDI95_0CS_400000raw_dir.qza --i-protein-alignment alignmentFiles_dir.qza --p-enriched-suffix
.. '_enriched.txt' --p-align-header 'AlignPos' --p-align-delim '~' --p-color-scheme 'viridis' --o-visualization testingProt
.. einHeatmap

Here we will test q2-ps-plot's proteinHeatmap module by running the following command:

.. usage::
   
   protHeatMap, = use.action(
      use.UsageAction(plugin_id="ps_plot", action_id="proteinHeatmap_dir"),
      use.UsageInputs(
        enriched_dir_filepath = "source/data/peptide_enrichment",
        protein_alignment_filepath = "source/data/prot_align/manifest.tsv",
        enriched_suffix = "_enriched.txt",
        align_header = "AlignPos",
        align_delim = "~",
        color_scheme = "viridis"
      ),
      use.UsageOutputNames(
        protein_heatmap_vis = "protein_heat_map"
      )
      )

Mutant Scatters
---------------

.. usage-selector::

Here we will test q2-ps-plot's mutantScatters module by running the following command:

.. usage::
     
   def metadata_factory():
      import qiime2
      return qiime2.Metadata.load("source/data/metadata.tsv")

   metadata = use.init_metadata('metadata', metadata_factory)

   def samples_factory():
        import qiime2
        return qiime2.Metadata.load("source/data/sample_source.tsv")

   samples = use.init_metadata('samples', samples_factory)

   def zscore_factory():
      import qiime2
      return qiime2.Artifact.load("source/data/zscores.qza")

   zscore = use.init_artifact("zscore", zscore_factory)

   def reference_factory():
      import qiime2
      return qiime2.Artifact.load("source/data/references.qza")

   reference = use.init_artifact("reference", reference_factory)
   
.. usage:: 

   samples_col = use.get_metadata_column('samples_col', 'Source', samples)

   mutantScatter, = use.action(
   use.UsageAction(plugin_id='ps_plot', action_id='mutantScatters'),
   use.UsageInputs(
        source = samples_col,
        metadata = metadata,
        zscore = zscore,
        reference_file = reference,
        peptide_header = "SampleID",
        reference_header = "Reference",
        x_axis_header = "Position",
        category_header = "Category1",
        label_header = "Label",
        wobble = True,
        scatter_boxplot = True
   ),
   use.UsageOutputNames(
        visualization = "mutant_scatter"
   )
   )
