Ps-qc Tutorials - CLI Edition (more to come)
============================================

Description
-----------

This guide is a preview of how you can use some of q2-ps-qc's individual modules.

Introduction
------------

In this tutorial you'll use QIIME 2 to perform an analysis of some data.

Generate a Correlation Matrix
-----------------------------

.. usage-selector::

.. qiime q2-ps-qc generate-corr-matrix --p-data IM0032-pA_PV1_subset_CS.tsv
.. --o-bad-output bad_corr
.. --o-good-output good_corr
.. --output-dir tut-ps-qc
.. --verbose > corr_mat_gen.out

Here we will test q2-ps-qc's generate-corr-matrix module by running the following command:

