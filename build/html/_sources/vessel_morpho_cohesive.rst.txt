.. _section-vessel-sediment-cohesive:

Single vessel + cohesive sediment 
####################################

In this example, you will add cohesive sediment morphology to a single vessel ship wakes example. The primary "input.txt" and :code:`vessel_00001` files are located in :code:`/simple_cases/single_vessel_cohesive/`. 

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

 If a "depth.txt" is not located in the working directory, you will need to run the "mk_depth.F" Fortran script to generate a depth file, which uses the "bathy_param.txt" file as an input. You can do this by typing the following into your terminal: :code:`gfortran mk_depth.f`. Refer to :ref:`definition_grid` for parameter definitions.

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
         TOTAL_TIME = 700.0
         PLOT_INTV = 5.0
         PLOT_INTV_STATION = 50000.0
         SCREEN_INTV = 5.0

 Keep the single vessel characteristics and sediment morphology parameters as :ref:`section-vessel-morpho-short` and somethng new for cohesive sediment

 .. code-block:: rest

  ! ------  Sediment
     Bed_Change = T
     BedLoad = F
     CohesiveSediment = T
     SoftBed = T
     E_coh = 0.0001
  ! use default values for following parameters (comment out them)
    !D50 = 0.000005
    !Sdensity = 2.68
    !n_porosity = 0.47
    !WS = 0.0125  it will be calcuated by a formula
    !Tan_phi = 0.7
    !Kappa1 = 0.3333
    !Kappa2 = 1.0
    !MinDepthPickup = 0.1

**Postprocessing**

For postprocessing examples, MATLAB scripts are located in :code:`/simple_cases/single_vessel_morphology/postprocessing/`. Example model results are shown below:

.. figure:: ../../FUNWAVE_GITHUB/FUNWAVE-TVD/simple_cases/single_vessel_cohesive/wakes_cohesive_sed.jpg

    Shipwakes and sediment concentration at different times.

.. figure:: ../../FUNWAVE_GITHUB/FUNWAVE-TVD/simple_cases/single_vessel_cohesive/wakes_cohesive_morpho.jpg

    Sediment concentration and bed change at t=600 sec.

.. figure:: ../../FUNWAVE_GITHUB/FUNWAVE-TVD/simple_cases/single_vessel_cohesive/section_mean_wave_morpho.jpg

    Bed change (upper) and wave envelope (lower) at t=600 sec.


