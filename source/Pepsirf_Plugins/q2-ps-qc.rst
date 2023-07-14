q2-ps-qc
========

Qiime2 Plug-in which allows users to run various quality control tests on files generated using PepSIRF (e.g. correlation measurements).

Dependencies
````````````
- qiime2-2021.11 +
- PepSIRF v1.4.0
- q2-pepsirf v2021.12
- q2-ps-plot v2021.9.15

Qiime2 installation documentation: https://docs.qiime2.org/2022.2/install/
PepSIRF installation documentation: https://github.com/LadnerLab/PepSIRF
q2-pepsirf installation documentation: https://ladnerlab.github.io/pepsirf-q2-plugin-docs/Pepsirf_Plugins/q2-pepsirf1/
q2-ps-plot installation documentation: https://ladnerlab.github.io/pepsirf-q2-plugin-docs/Pepsirf_Plugins/q2-ps-plot/

Installation
------------
First, make sure to enable your Qiime2 Conda environment:

``conda activate qiime2-2021.11``

You may replace `qiime2-2021.11` with a different version of Qiime2 you have installed

Next, to install the QC module, run the following command:

``pip install git+https://github.com/LadnerLab/q2-ps-qc.git``

Finally, run ``qiime2 info`` to check for a successful installation. If installation was successful, you will see ``q2-ps-qc: (version)`` in the list of installed plugins

Updating
--------
To update the QC module, run the following command:

``pip install -U git+https://github.com/LadnerLab/q2-ps-qc.git``

