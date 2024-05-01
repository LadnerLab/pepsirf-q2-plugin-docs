q2-autopepsirf
==============

Qiime2 plugin used for the automation of q2-pepsirf and
q2-ps-plot.

Installation
------------


Dependencies:
`````````````

- ``qiime2-2021.11``
- ``q2-pepsirf v2021.12``
- ``q2-ps-plot v2021.9.15``
- ``PepSIRF v1.4.0``
- ``altair v4.1.0``
- ``altair_saver v0.5.0``
- ``jsonschema 3.2``

Qiime2 Installation:
````````````````````

Visit: https://docs.qiime2.org/2022.2/install/ for intallation documentation on Qiime2

PepSIRF Installation:
``````````````````````

Visit: https://github.com/LadnerLab/PepSIRF for installation documentation on PepSIRF

q2-pepsirf Installation:
`````````````````````````

Visit: https://ladnerlab.github.io/pepsirf-q2-plugin-docs/Pepsirf_Plugins/q2-pepsirf1/ 
for installation documentation on q2-pepsirf

q2-ps-plot Installation:
`````````````````````````

Visit: https://ladnerlab.github.io/pepsirf-q2-plugin-docs/Pepsirf_Plugins/q2-ps-plot/ 
for installation documentation on q2-ps-plot

q2-autopepsirf Installation:
````````````````````````````

Make sure your Qiime2 conda environment is activated by running the command: 

``conda activate qiime2-2021.11``

You can replace qiime2-2021.11 above with whichever version of QIIME 2 you have currently installed.

Now you are ready to install q2-autopepsirf. Run the following commands:

``pip install git+https://github.com/LadnerLab/q2-autopepsirf.git``

Run qiime info to check for a successful installation. If installation was successful, you should see autopepsirf: version in the list of installed plugins.

Typical Run Time: 4.43 Seconds

Updating
--------

To update q2-autopepsirf, run the following command:

``pip install -U git+https://github.com/LadnerLab/q2-autopepsirf.git``
