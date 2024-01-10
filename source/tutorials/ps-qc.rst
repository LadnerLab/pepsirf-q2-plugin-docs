Ps-qc Tutorials - CLI Edition (more to come)
============================================

Description
-----------

This guide is a preview of how you can use some of q2-ps-qc's individual modules.

Introduction
------------

In this tutorial you'll use QIIME 2 to perform an analysis of some data.

Typical Runtime: 0 Minutes 15.43 Seconds

Generate a Correlation Matrix
-----------------------------

.. usage-selector::

.. qiime q2-ps-qc generate-corr-matrix --p-data IM0032-pA_PV1_subset_CS.tsv
.. --output-dir tut-ps-qc
.. --verbose > corr_mat_gen.out

Here we will test q2-ps-qc's generate-corr-matrix module by running the following command:

.. usage::

	bad_corr_vis, good_corr_vis = use.action(
		use.UsageAction(
			plugin_id="q2_ps_qc",
			action_id="generate_corr_matrix"
		),
		use.UsageInputs(
			data="source/data/IM0032-pA_PV1_subset_CS.tsv"
		),
		use.UsageOutputNames(
			bad_output="bad_corr",
			good_output="good_corr"
		)
	)
