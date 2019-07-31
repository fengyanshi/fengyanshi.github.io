.. _section-vessel-sediment-single:

Single vessel + sediment 
########################

In this example, you will add sediment morphology to a single vessel ship wakes example. The primary "input.txt" and :code:`vessel_00001` files are located in :code:`/simple_cases/single_vessel_morphology/`. 

**Model setup**

.. figure:: images/simple_cases/layout_single_vessel.jpg
    :width: 500px
    :align: center
    :height: 120px
    :alt: alternate text
    :figclass: align-center


**Setup "input.txt"**

This example is slightly different from the previous example described in :ref:`section-vessel-morpho-short`. Update the following sections:

Set a descriptive title for your simulation:

 .. code-block:: rest

        !-----TITLE-----
         TITLE = vessel_sediment_morph

 If running in parallel, set the number of processors in X and Y:

 .. code-block:: rest

        !-----PARALLEL INFO-----
         PX = 4 
         PY = 1

 Set the bathymetry to the provided depth file: 

 .. code-block:: rest

        !-----DEPTH-----
         DEPTH_TYPE = DATA
         DEPTH_FILE = ./depth.txt

 If a "depth.txt" is not located in the working directory, you will need to run the "mk_depth.f" Fortran script to generate a depth file, which uses the "bathy_param.txt" file as an input. You can do this by typing the following into your terminal: :code:`gfortran mk_depth.f`. Refer to :ref:`definition_grid` for parameter definitions.

 Send the results to a folder named "output":

 .. code-block:: rest

        !-----PRINT-----
         RESULT_FOLDER = output/

 Set the dimension of the domain to 2400 x 60 (x and y directions, respectively):

 .. code-block:: rest

        !-----DIMENSION-----
         Mglob = 2400
         Nglob = 60

 Set the computational time, plot time, station printing interval, and screen interval to 2000.0 s, 5.0 s, 50,000.0 s, and 5.0 s, respectively:

 .. code-block:: rest

        !-----TIME-----
         TOTAL_TIME = 2000.0
         PLOT_INTV = 5.0
         PLOT_INTV_STATION = 50000.0
         SCREEN_INTV = 5.0

 Keep the single vessel characteristics and sediment morphology parameters as :ref:`section-vessel-morpho-short`.

**Postprocessing**

For postprocessing examples, MATLAB and Python scripts are located in :code:`/simple_cases/single_vessel_morphology/postprocessing/`. An example model result is shown below:

.. figure:: images/simple_cases/single_wave_conc.jpg
    :width: 400px
    :align: center
    :height: 600px
    :alt: alternate text
    :figclass: align-center

    Shipwakes and sediment concentration at different times.


