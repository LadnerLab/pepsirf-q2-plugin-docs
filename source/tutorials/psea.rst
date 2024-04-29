PSEA Tutorials - CLI Edition (more to come)
===========================================

Description
-----------

This guide is a preview of how you can use some of the q2-PSEA's individual modules.

Intorudction
------------

In this tutorial you'll use QIIME 2 to perform an analysis of some data.

Typical Runtime:

Generate Visualizations of PSEA results
---------------------------------------

.. usage-selector::

.. qiime psea make-psea-table --p-scores-file source/data/psea-example/IM0031_PV2T_25nt_raw_2mm_i1mm_Z-HDI75.tsv
.. --p-pairs-file source/data/psea-example/pairs.tsv
.. --p-peptide-sets-file source/data/psea-example/input.gmt
.. --p-species-taxa-file source/data/psea-example/species_taxa.tsv
.. --p-threshold 0.750000
.. --p-min-size 3
.. --p-max-size 5000
.. --p-permutation-num 10000
.. --p-table-dir psea-example-tables
.. --output-dir psea-example-outdir

Here we will test q2-PSEA's generate-vis module by running the following command:

.. usage::

	scatter_plot, volcano_plot = use.action(
		use.UsageAction(
			plugin_id="psea",
			action_id="make_psea_table"
		),
		use.UsageInputs(
			scores_file="source/data/IM0031_PV2T_25nt_raw_2mm_i1mm_Z-HDI75.tsv",
			pairs_file="source/data/pairs.tsv",
			peptide_sets_file="source/data/input.gmt",
			threshold=0.750000,
			species_taxa_file="source/data/species_taxa.tsv",
			min_size=3,
			max_size=5000,
			permutation_num=10000,
			table_dir="psea-example-tables"
		),
		use.UsageOutputNames(
			scatter_plot="scatter_plot",
			volcano_plot="volcano_plot"
		)
	)
