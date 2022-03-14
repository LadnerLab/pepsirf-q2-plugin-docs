PepSIRF Qiime 2 Plugin tutorial - Multiple Interface Edition
============================================================

Description
-----------

This guide is a preview of how you can use q2-pepsirf and q2-autopepsirf.

Introduction
------------

In this tutorial you'll use QIIME 2 to perform an analysis of some data.

Typical Run Time: 5 Minutes

Sample Raw Data
---------------

.. usage-selector::

Before starting the analysis, download the raw data and bin files. These
``IM0032-pA_PV1_subset.qza``, ``pA_PV1.5_r1bins_IM25-26.qza``, and 
``samples_source.tsv`` files are used throughout the rest of the tutorial.

.. usage::
  
   def raw_factory():
      import qiime2
      return qiime2.Artifact.load("source/data/IM0032-pA_PV1_subset.qza")

   raw_data = use.init_artifact("IM0032-pA_PV1_subset", raw_factory)

   def bin_factory():
      import qiime2
      return qiime2.Artifact.load("source/data/pA_PV1.5_r1bins_IM25-26.qza")

   bin_data = use.init_artifact("pA_PV1.5_r1bins_IM25-26", bin_factory)

   def metadata_factory():
      import qiime2
      return qiime2.Metadata.load("source/data/samples_source.tsv")

   metadata = use.init_metadata('samples_source', metadata_factory)

All data that is used as input to QIIME 2 is in form of QIIME 2 artifacts,
which contain information about the type of data and the source of the data.

Autopepsirf Automation
----------------------

.. usage-selector::

Once you have downloaded the file, you can automatically run q2-pepsirf and 
q2-ps-plot with q2-autopepsirf. This can be done by running the following 
command (replace pepsirf_binary with how you call pepsirf on your machine):

.. usage::

    col_sum, diff, diff_ratio, zscore, zscore_nan, sample_names, read_counts, rcBoxplot, enriched, enrichBoxplot, zScatter, csScatter, zenrich = use.action(
    use.UsageAction(plugin_id='autopepsirf', action_id='diffEnrich'),
    use.UsageInputs(
        raw_data = raw_data,
        bins = bin_data,
        negative_id = "SB_",
        exact_z_thresh = "6,10",
        pepsirf_tsv_dir = "./testingTSV",
        tsv_base_str = "IM0032-pA_PV1_subset",
        hdi = 0.95,
        pepsirf_binary = "/mnt/c/Users/ANNAB/Documents/GitHub/PepSIRF/precompiled/linux_mint_19.3/pepsirf_1.4.0_linux"
    ),
    use.UsageOutputNames(
        col_sum = "colsum",
        diff = "diff",
        diff_ratio = "diff_ratio",
        zscore = "zscore",
        zscore_nan = "zscore_nan",
        sample_names = "sample_names",
        read_counts = "read_counts",
        rc_boxplot = "rcBoxplot",
        enrich = "enrich",
        enrich_count_boxplot = "enrichBoxplot",
        zscore_scatter = "zScatter",
        colsum_scatter = "csScatter",
        zenrich_scatter = "zenrich"
    )
    ) 

.. note::
    TSV/PNG outputs will not show up on this page. They are just duplicates of the .qza files in a .tsv format.

Pepsirf Normalization
---------------------

.. usage-selector::

You can also run q2-pepsirf and q2-ps-plot by themseleves to get
individual files. Here we wil test q2-pepsirf's norm module by 
running the following command (replace pepsirf_binary with how you 
call pepsirf on your machine):

.. usage::

   col_sum, = use.action(
    use.UsageAction(plugin_id='pepsirf', action_id='norm'),
    use.UsageInputs(
        peptide_scores = raw_data,
        pepsirf_binary = "/mnt/c/Users/ANNAB/Documents/GitHub/PepSIRF/precompiled/linux_mint_19.3/pepsirf_1.4.0_linux"
    ),
    use.UsageOutputNames(
        qza_output = "IM0032-pA_PV1_subset_CS"
    )
    )

Pepsirf bin
-----------

.. usage-selector::

Here we wil test q2-pepsirf's bin module by 
running the following command (replace pepsirf_binary with how you 
call pepsirf on your machine):

.. usage::

   pepsirf_bin, = use.action(
    use.UsageAction(plugin_id='pepsirf', action_id='bin'),
    use.UsageInputs(
        scores = col_sum,
        bin_size = 300,
        round_to = 0,
        pepsirf_binary = "/mnt/c/Users/ANNAB/Documents/GitHub/PepSIRF/precompiled/linux_mint_19.3/pepsirf_1.4.0_linux"
    ),
    use.UsageOutputNames(
        bin_output = "IM0032-pA_PV1_subset_bin"
    )
    )

Ps-plot repScatters
-------------------

.. usage-selector::

Here we will test q2-ps-plot's repScatters module by running the following command:

.. usage::

   samples_col = use.get_metadata_column('samples_col', 'source', metadata)

   zScatter, = use.action(
    use.UsageAction(plugin_id='ps_plot', action_id='repScatters'),
    use.UsageInputs(
        zscore = zscore,
        source = samples_col,
    ),
    use.UsageOutputNames(
        visualization = "ZRepScatter"
    )
    )

Ps-plot zenrich
-------------------

.. usage-selector::

Here we will test q2-ps-plot's zenrich module by running the following command
(replace pepsirf_binary with how you call pepsirf on your machine):

.. usage::

   zenrichScat, = use.action(
    use.UsageAction(plugin_id='ps_plot', action_id='zenrich'),
    use.UsageInputs(
        data = col_sum,
        zscores = zscore,
        source = samples_col,
        negative_controls = ["SB_pA_A","SB_pA_B","SB_pA_D"],
        pepsirf_binary = "/mnt/c/Users/ANNAB/Documents/GitHub/PepSIRF/precompiled/linux_mint_19.3/pepsirf_1.4.0_linux"
    ),
    use.UsageOutputNames(
        visualization = "zenrich_scatter"
    )
    )
