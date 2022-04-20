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

.. note::
   You must have the development branch of pepsirf precompiled in order to use this module.