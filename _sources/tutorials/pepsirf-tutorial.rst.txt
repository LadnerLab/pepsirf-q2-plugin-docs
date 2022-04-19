DiffEnrich Analysis Tutorial - Multiple Interface Edition
============================================================

Description
-----------

This guide is a preview of how you can use q2-autopepsirf's diffEnrich module, along with how to use
the individual modules of q2-pepsirf and q2-ps-plot to accomplish a diffEnrich analysis.

Introduction
------------

In this tutorial you'll use QIIME 2 to perform an analysis of some data.

Typical Run Time: 12 Minutes

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
        pepsirf_binary = "pepsirf"
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
        pepsirf_binary = "pepsirf"
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
        pepsirf_binary = "pepsirf"
    ),
    use.UsageOutputNames(
        bin_output = "IM0032-pA_PV1_subset_bin"
    )
    )

Pepsirf zscore
--------------

.. usage-selector::

Here we wil test q2-pepsirf's zscore module by 
running the following command (replace pepsirf_binary with how you 
call pepsirf on your machine):

.. usage::

   pepsirf_zscore, pepsirf_nan, = use.action(
    use.UsageAction(plugin_id='pepsirf', action_id='zscore'),
    use.UsageInputs(
        scores = diff,
        bins = bin_data,
        hdi = 0.95,
        pepsirf_binary = "/mnt/c/Users/ANNAB/Documents/GitHub/PepSIRF/precompiled/linux_mint_19.3/pepsirf_1.4.0_linux"
    ),
    use.UsageOutputNames(
        zscore_output = "IM0032-pA_PV1_Z-HDI95",
        nan_report = "IM0032-pA_PV1_Z-HDI95_nan"
    )
    )

Pepsirf infoSNPN
----------------

.. usage-selector::

Here we wil test q2-pepsirf's infoSNPN module by 
running the following command (replace pepsirf_binary with how you 
call pepsirf on your machine):

.. usage::

   pepsirf_sample_names, = use.action(
    use.UsageAction(plugin_id='pepsirf', action_id='infoSNPN'),
    use.UsageInputs(
        input = raw_data,
        get = "samples",
        pepsirf_binary = "/mnt/c/Users/ANNAB/Documents/GitHub/PepSIRF/precompiled/linux_mint_19.3/pepsirf_1.4.0_linux"
    ),
    use.UsageOutputNames(
        snpn_output = "IM0032-pA_PV1_SN",
    )
    )

Pepsirf infoSumOfProbes
-----------------------

.. usage-selector::

Here we wil test q2-pepsirf's infoSumOfProbes module by 
running the following command (replace pepsirf_binary with how you 
call pepsirf on your machine):

.. usage::

   pepsirf_read_counts, = use.action(
    use.UsageAction(plugin_id='pepsirf', action_id='infoSumOfProbes'),
    use.UsageInputs(
        input = raw_data,
        pepsirf_binary = "/mnt/c/Users/ANNAB/Documents/GitHub/PepSIRF/precompiled/linux_mint_19.3/pepsirf_1.4.0_linux"
    ),
    use.UsageOutputNames(
        sum_of_probes_output = "IM0032-pA_PV1_RC",
    )
    )

Pepsirf enrich
--------------

.. usage-selector::

Here we wil test q2-pepsirf's enrich module by 
running the following command (replace pepsirf_binary with how you 
call pepsirf on your machine):

.. usage::

    samples_col = use.get_metadata_column('samples_col', 'source', metadata)

    pepsirf_enrich_dir, = use.action(
    use.UsageAction(plugin_id='pepsirf', action_id='enrich'),
    use.UsageInputs(
        source = samples_col,
        zscores = zscore,
        col_sum = col_sum,
        exact_z_thresh = "6,10",
        exact_cs_thresh = "20",
        enrichment_failure = True,
        pepsirf_binary = "/mnt/c/Users/ANNAB/Documents/GitHub/PepSIRF/precompiled/linux_mint_19.3/pepsirf_1.4.0_linux"
    ),
    use.UsageOutputNames(
        dir_fmt_output = "6-10Z-HDI95_20CS_300000raw",
    )
    )

Ps-plot readCountsBoxplot
-------------------------

.. usage-selector::

Here we will test q2-ps-plot's readCountsBoxplot module by running the following command:

.. usage::

   zScatter, = use.action(
    use.UsageAction(plugin_id='ps_plot', action_id='readCountsBoxplot'),
    use.UsageInputs(
        read_counts = read_counts
    ),
    use.UsageOutputNames(
        visualization = "RCBoxplot"
    )
    )

Ps-plot enrichmentRCBoxplot
---------------------------

.. usage-selector::

Here we will test q2-ps-plot's enrichmentRCBoxplot module by running the following command:

.. usage::

   zScatter, = use.action(
    use.UsageAction(plugin_id='ps_plot', action_id='enrichmentRCBoxplot'),
    use.UsageInputs(
        enriched_dir = enriched
    ),
    use.UsageOutputNames(
        visualization = "enrichedBoxplot"
    )
    )

Ps-plot repScatters
-------------------

.. usage-selector::

Here we will test q2-ps-plot's repScatters module by running the following command:

.. usage::

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
---------------

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
        pepsirf_binary = "pepsirf"
    ),
    use.UsageOutputNames(
        visualization = "zenrich_scatter"
    )
    )

