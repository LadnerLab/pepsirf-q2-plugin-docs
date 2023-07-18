q2-ps-qc
========

Qiime2 Plug-in which allows users to run various quality control tests on files generated using PepSIRF (e.g. correlation measurements).

Installation
------------

Dependencies
````````````
- ``qiime2-2021.11 +``
- ``PepSIRF v1.4.0``
- ``q2-pepsirf v2021.12``
- ``q2-ps-plot v2021.9.15``

Qiime2 Installation
```````````````````
Visit: https://docs.qiime2.org/2022.2/install/ for installation documentation on Qiime2

PepSIRF Installation:
`````````````````````

Visit: https://github.com/LadnerLab/PepSIRF for installation documentation on PepSIRF

q2-pepsirf Installation:
````````````````````````

Visit: https://ladnerlab.github.io/pepsirf-q2-plugin-docs/Pepsirf_Plugins/q2-pepsirf1/
for installation documentation on q2-pepsirf

q2-ps-plot Installation:
````````````````````````

Visit: https://ladnerlab.github.io/pepsirf-q2-plugin-docs/Pepsirf_Plugins/q2-ps-plot/
for installation documentation on q2-ps-plot

q2-ps-qc Installation:
``````````````````````

Make sure your Qiime2 conda environment is activated by running the command:

``conda activate qiime2-2021.11``

You can replace qiime2-2021.11 above with whichever version of QIIME 2 you have currently installed.

Now you are ready to install ps-qc. Run the following commands:

``pip install git+https://github.com/LadnerLab/q2-ps-qc.git``

Run ``qiime2 info`` to check for a successful installation. If installation was successful, you will see ``q2-ps-qc: (version)`` in the list of installed plugins

Updating
--------
To update the QC module, run the following command:

``pip install -U git+https://github.com/LadnerLab/q2-ps-qc.git``

