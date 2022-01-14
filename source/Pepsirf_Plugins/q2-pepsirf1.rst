q2-pepsirf
==========

Qiime2 Plug-in for the use of pepsirf within qiime.

Installation
------------


Dependencies:
`````````````

- ``qiime2-2021.11 +``
- ``PepSIRF``

Qiime2 Installation:
`````````````````````

Visit: https://docs.qiime2.org/2021.8/install/ for intallation documentation on Qiime2

PepSIRF Installation:
`````````````````````

Visit: https://github.com/LadnerLab/PepSIRF for installation documentation on PepSIRF

q2-pepsirf Installation:
`````````````````````````

Make sure your Qiime2 conda environment is activated by running the command:

``conda activate qiime2-2021.11``

You can replace qiime2-2021.11 above with whichever version of QIIME 2 you have currently installed. 

Now you are ready to install q2-pepsirf. Run the following commands:

``pip install git+https://github.com/LadnerLab/q2-pepsirf.git``

Run qiime info to check for a successful installation. If installation was successful, you should see pepsirf: version in the list of installed plugins.

Updating
--------

To update q2-pepsirf, run the following command:

``pip install -U git+https://github.com/LadnerLab/q2-pepsirf.git``
