q2-ps-plot
==========

Qiime2 Plug-in for the creation of visualizations 
from PepSIRF outputs.

Installation
------------

Dependencies:
`````````````

- ``qiime2-2021.11 +``
- ``q2-pepsirf``
- ``PepSIRF``
- ``altair``
- ``altair_saver``
- ``jsonschema 3.2``

Qiime2 Installation:
````````````````````

Visit: https://docs.qiime2.org/2021.8/install/ for intallation documentation on Qiime2

PepSIRF Installation:
``````````````````````

Visit: https://github.com/LadnerLab/PepSIRF for installation documentation on PepSIRF

q2-pepsirf Installation:
````````````````````````

Visit: https://ladnerlab.github.io/pepsirf-q2-plugin-docs/Pepsirf_Plugins/q2-pepsirf1/ 
for installation documentation on q2-pepsirf

q2-ps-plot Installation:
`````````````````````````

Make sure your Qiime2 conda environment is activated by running the command:

``conda activate qiime2-2021.11``

You can replace qiime2-2021.11 above with whichever version of QIIME 2 you have currently installed.

Now you are ready to install ps-plot. Run the following commands:

``conda install -c conda-forge altair altair_saver``

``pip install jsonschema==3.2``

``pip install git+https://github.com/LadnerLab/q2-ps-plot.git``

Run qiime info to check for a successful installation. If installation was successful, you should see ps-plot: version in the list of installed plugins.

Updating
--------

To update ps-plot, run the following command:

``pip install -U git+https://github.com/LadnerLab/q2-ps-plot.git``


