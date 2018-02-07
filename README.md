# README #

### How do I get set up? ###

To avoid problems with installation, use of the virtualenv Python virtual environment is recommended.

Then use pip to install all dependencies (numpy, scipy, matplotlib, netCDF4, cython, pyproj, Shapely, ...), e.g.:

* ** pip install cython numpy matplotlib scipy netCDF4 shapely pyproj**

Then run the following to install the eddy tracker:

* ** python setup.py install**

Two executables are now available in your PATH: EddyIdentification and EddyTracking

Edit the corresponding yaml files and then run the code, e.g.:

* ** EddyIdentification eddy_identification.yaml**

for identification, followed by:

* ** EddyTracking tracking.yaml**

for tracking.