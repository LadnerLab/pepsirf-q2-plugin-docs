q2-PSEA
=======

Qiime2 plugin used to accomplish Peptide Set Enrichment Analysis (PSEA) and
visualize results.

Installation
------------


Dependencies:
`````````````

- ``qiime2-2023.7 or later``
- ``q2-pepsirf``
- ``q2-ps-plot``
- ``altair v5.0.0``
- ``altair_saver v0.5.0``
- ``rpy2 v3.5.11 or later``

R Dependencies:
```````````````

- ``r-base``
- ``r-essentials``
- ``r-igraph``
- ``r-ggraph``
- ``r-ggforce``
- ``r-scatterpie``
- ``r-ggplot2 v3.3``
- ``pillow v9.4``
- ``r-biocmanager``
- ``bioconductor-ggtree``
- ``bioconductor-enrichplot``
- ``bioconductor-clusterprofiler``

Qiime2 Installation:
````````````````````

Visit: https://docs.qiime2.org/2022.2/install/ for intallation documentation on Qiime2


q2-pepsirf Installation:
````````````````````````

Visit: https://ladnerlab.github.io/pepsirf-q2-plugin-docs/Pepsirf_Plugins/q2-pepsirf1/ 
for installation documentation on q2-pepsirf


q2-ps-plot Installation:
`````````````````````````

Visit: https://ladnerlab.github.io/pepsirf-q2-plugin-docs/Pepsirf_Plugins/q2-ps-plot/ 
for installation documentation on q2-ps-plot


q2-PSEA Installation:
`````````````````````

Make sure your Qiime2 conda environment is activated by running the command: 

``conda activate qiime2-2023.7``

You can replace qiime2-2023.7 above with whichever version of QIIME 2 you have currently installed.

To help make installing R dependencies easier, please use this command if you have trouble:
``conda install -c conda-forge r-base r-essentials rpy2 r-biocmanager``
``conda install -c conda-forge bioconductor-clusterprofiler``

You will need to install clusterProfiler through R to avoid conflicting versions with some packages:
Please download the custom R script to do so here: https://github.com/LadnerLab/q2-PSEA/blob/main/install_r_packages.R
``Rscript path/to/install_r_packages.R``
``rm path/to/install_r_packages.R``

Now you are ready to install q2-PSEA. Run the following commands:

``pip install git+https://github.com/LadnerLab/q2-PSEA.git``

Run qiime info to check for a successful installation. If installation was successful, you should see psea: version in the list of installed plugins.

Using provided example data, average run time for 3 trials was: 76.823s

Updating
--------

To update q2-PSEA, run the following command:

``pip install -U git+https://github.com/LadnerLab/q2-PSEA.git``
