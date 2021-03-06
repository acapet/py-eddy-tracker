========
Tracking
========

Requirements
************

Before to run tracking, you will need to run identification on every time step of the period(Period of your study).

**Advice** : Before to run tracking, display some identification file allow to learn a lot

Default method
**************

To run a tracking just create an yaml file with minimal specification (*FILES_PATTERN* and *SAVE_DIR*).
You will run tracking separately between Cyclonic eddies and Anticyclonic eddies.

Example of conf.yaml

.. code-block:: yaml

    PATHS:
      # Files produces with EddyIdentification
      FILES_PATTERN: MY_IDENTIFICATION_PATH/Anticyclonic*.nc
      SAVE_DIR: MY_OUTPUT_PATH

    # Number of timestep for missing detection
    VIRTUAL_LENGTH_MAX: 3
    # Minimal time to consider as a full track
    TRACK_DURATION_MIN: 10

To run:

.. code-block:: bash

    EddyTracking conf.yaml -v DEBUG

It will use default tracker:

- No travel longer than 125 km between two observation
- Amplitude and speed radius must be close to previous observation
- In case of several candidate only closest is kept


It will produce 4 files by run:

- A file of correspondances which will contains all the information to merge all identifications file
- A file which will contains all the observations which are alone
- A file which will contains all the short track which are shorter than **TRACK_DURATION_MIN**
- A file which will contains all the long track which are longer than **TRACK_DURATION_MIN**

Use python module
*****************

An example of tracking with python module is available in the gallery:
:ref:`sphx_glr_python_module_08_tracking_manipulation_pet_run_a_tracking.py`

Choose a tracker
****************

With yaml you could also select another tracker:

.. code-block:: yaml

    PATHS:
      # Files produces with EddyIdentification
      FILES_PATTERN: MY/IDENTIFICATION_PATH/Anticyclonic*.nc
      SAVE_DIR: MY_OUTPUT_PATH

    # Number of timestep for missing detection
    VIRTUAL_LENGTH_MAX: 3
    # Minimal time to consider as a full track
    TRACK_DURATION_MIN: 10

    CLASS:
        # Give the module to import,
        # must be available when you do "import module" in python
        MODULE: py_eddy_tracker.featured_tracking.old_tracker_reference
        # Give class name which must be inherit from
        # py_eddy_tracker.observations.observation.EddiesObservations
        CLASS: CheltonTracker

This tracker is like described in CHELTON11[https://doi.org/10.1016/j.pocean.2011.01.002].
Code is here :meth:`py_eddy_tracker.featured_tracking.old_tracker_reference`
