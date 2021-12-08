"q2-pepsirf and q2-autopepsirf" tutorial - Multiple Interface Edition
=====================================================================

Description
-----------

This guide is a preview of how you can use q2-pepsirf and q2-autopepsirf.

Introduction
------------

In this tutorial you'll use QIIME 2 to perform an analysis of some data.

Sample Raw Data
---------------

.. usage-selector::

Before starting the analysis, download the raw data and bin files. These
``IM0032-pA_PV1_subset.qza`` and ``pA_PV1.5_r1bins_IM25-26.qza`` 
files are used throughout the rest of the tutorial.

.. usage::
  
   def raw_factory():
      import qiime2
      return qiime2.Artifact.load("source/data/IM0032-pA_PV1_subset.qza")

   raw_data = use.init_artifact("IM0032-pA_PV1_subset", raw_factory)

   def bin_factory():
      import qiime2
      return qiime2.Artifact.load("source/data/pA_PV1.5_r1bins_IM25-26.qza")

   bin_data = use.init_artifact("pA_PV1.5_r1bins_IM25-26", bin_factory)

All data that is used as input to QIIME 2 is in form of QIIME 2 artifacts,
which contain information about the type of data and the source of the data.

Autopepsirf Automation
----------------------

.. usage-selector::

Once you have downloaded the file, you can automatically run q2-pepsirf and 
q2-ps-plot with q2-autopepsirf. This can be done by running the following 
command:

.. usage::

    col_sum, diff, diff_ratio, zscore, zscore_nan, sample_names, read_counts, rcBoxplot, enriched, enrichBoxplot, zScatter, csScatter, zenrich = use.action(
    use.UsageAction(plugin_id='autopepsirf', action_id='diffEnrich'),
    use.UsageInputs(
        raw_data = raw_data,
        bins = bin_data,
        negative_id = "SB_",
        exact_z_thresh = "6,10",
        pepsirf_binary = "/mnt/c/Users/ANNAB/Documents/GitHub/PepSIRF/precompiled/linux_mint_19.3/pepsirf_1.4.0_linux"
    ),
    use.UsageOutputNames(
        col_sum = "colsum1",
        diff = "diff1",
        diff_ratio = "diff_ratio1",
        zscore = "zscore1",
        zscore_nan = "zscore_nan1",
        sample_names = "sample_names1",
        read_counts = "RC1",
        rc_boxplot = "rcBoxplot1",
        enrich = "enrichDir1",
        enrich_count_boxplot = "enrichBoxplot1",
        zscore_scatter = "zScatter1",
        colsum_scatter = "csScatter1",
        zenrich_scatter = "zenrich1"
    )
    ) 

Pepsirf Normalization
---------------------

.. usage-selector::

You can also run q2-pepsirf and q2-ps-plot by themseleves to get
individual files. Here we wil test q2-pepsirf's norm module by 
running the following command:

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

Ps-plot tutorial
----------------

A q2-ps-plot zenrich module tutorial can be located here:
https://github.com/LadnerLab/q2-ps-plot.git