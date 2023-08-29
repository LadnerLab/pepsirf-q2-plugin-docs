q2-pepsirf Tutorials - Multiple Interface Edition
=================================================

Description
-----------

This guide is a preview of how you can use some of q2-pepsirf's individual modules.

Introduction
------------

In this tutorial you'll use QIIME 2 to perform an analysis of some data.

Typical Run Time: TBD Minute

Demux
-----

.. usage-selector::

Here we will test q2-pepsirf's demux module by running the following command:

.. note::
   You must have the development branch of pepsirf precompiled in order to use this module.

.. usage::

   def r1_factory():
      import qiime2
      return qiime2.Artifact.load("source/data/Undetermined_S0_R1_001_1M.qza")

   input_r1 = use.init_artifact("input_r1", r1_factory)

   def r2_factory():
      import qiime2
      return qiime2.Artifact.load("source/data/Undetermined_S0_I1_001_1M.qza")

   input_r2 = use.init_artifact("input_r2", r2_factory)

   def fif_factory():
      import qiime2
      return qiime2.Artifact.load("source/data/demux_flex_2indexes_test.qza")

   fif = use.init_artifact("fif", fif_factory)

   def library_factory():
      import qiime2
      return qiime2.Artifact.load("source/data/noDupEncode_NS64_coded_116nt.qza")

   library = use.init_artifact("library", library_factory)

   def sample_factory():
      import qiime2
      return qiime2.Artifact.load("source/data/NS64_sample_list_extended.qza")

   samplelist = use.init_artifact("sample_list", sample_factory)

   def index_factory():
      import qiime2
      return qiime2.Artifact.load("source/data/BSC_FR_barcodes_Plus.qza")

   index = use.init_artifact("index", index_factory)
   
.. usage:: 

   rawData, diagnosticData,  = use.action(
   use.UsageAction(plugin_id='pepsirf', action_id='demux'),
   use.UsageInputs(
        input_r1 = input_r1,
        input_r2 = input_r2,
        fif = fif,
        seq = "43,116,2",
        read_per_loop = 200000,
        num_threads = 2,
        phred_base = 33,
        library = library,
        index =  index,
        samplelist = samplelist
   ),
   use.UsageOutputNames(
        raw_counts_output = "demux_diagnostic_output",
        diagnostic_output = "demux_2index_fif_output"
   )
   )

Deconv-Batch
------------

.. usage-selector::

Here we will test q2-pepsirf's deconv-batch module by running the following commands:

.. usage::

   def enriched_factory():
      import qiime2
      return qiime2.Artifact.load("source/data/pEnrich_z6-10_sbdr4_n20_r244k_dir.qza")

   enriched_dir = use.init_artifact("enriched_dir", enriched_factory)

   def linked_factory():
      import qiime2
      return qiime2.Artifact.load("source/data/full_design_clean_min30_taxtweak_100perc_jingmens_2020-11-23_K7-species.qza")

   linked = use.init_artifact("linked", linked_factory)

   def id_factory():
      import qiime2
      return qiime2.Artifact.load("source/data/virus_lineage.qza")

   id_name_map = use.init_artifact("id_name_map", id_factory)

.. note::
   Some of these files will also be used for deconv-singular.
   
.. usage:: 

   deconv, score_per_round, peptide_assignment_map,  = use.action(
   use.UsageAction(plugin_id='pepsirf', action_id='deconv_batch'),
   use.UsageInputs(
        enriched_dir = enriched_dir,
        score_filtering = True,
        threshold = 40,
        score_tie_threshold = 0.95,
        score_overlap_threshold = 0.7,
        remove_file_types = True,
        outfile_suffix = "_ss40.txt",
        mapfile_suffix = "_ss40.map",
        linked = linked,
        id_name_map = id_name_map
   ),
   use.UsageOutputNames(
        deconv_output = "deconv_output",
        score_per_round = "score_per_round",
        peptide_assignment_map = "peptide_assignment_map"
   )
   )

Deconv-Singular
---------------

.. usage-selector::

Here we will test q2-pepsirf's deconv-singular module by running the following commands:

.. usage::

   def peptide_factory():
      import qiime2
      return qiime2.Artifact.load("source/data/enriched-peptides.qza")

   enriched_peptides = use.init_artifact("enriched_peptides", peptide_factory)
   
.. usage:: 

   deconv_sing, score_per_round_sing,  = use.action(
   use.UsageAction(plugin_id='pepsirf', action_id='deconv_singular'),
   use.UsageInputs(
        enriched = enriched_peptides,
        score_filtering = True,
        threshold = 40,
        score_tie_threshold = 0.95,
        score_overlap_threshold = 0.7,
        linked = linked,
        id_name_map = id_name_map
   ),
   use.UsageOutputNames(
        deconv_output = "deconv_output_singular",
        score_per_round = "score_per_round_singular"
   )
   )
